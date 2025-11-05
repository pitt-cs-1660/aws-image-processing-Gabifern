FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

WORKDIR /var/task

# copy dependency spec and install (resolve deps without pre-existing lock)
COPY pyproject.toml ./
RUN uv sync --no-dev

# copy handler code
COPY handler.py ./

# ensure dependencies are importable
ENV PYTHONPATH=/var/task/.venv/lib/python3.13/site-packages

# set handler
CMD ["handler.exif_handler"]
