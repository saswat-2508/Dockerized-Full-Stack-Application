FROM mcr.microsoft.com/devcontainers/python:3.11

WORKDIR /app

RUN adduser --disabled-password appuser

COPY requirements.txt .

# Install with higher timeout and trusted hosts (fix network issues)
RUN pip install --no-cache-dir \
    --default-timeout=300 \
    --trusted-host pypi.org \
    --trusted-host files.pythonhosted.org \
    -r requirements.txt

COPY . .

RUN chown -R appuser:appuser /app

USER appuser

EXPOSE 8000

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
