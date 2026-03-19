FROM python:3.9-slim

WORKDIR /app

# Install system dependencies for YOLO/OpenCV
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
# Explicitly add ultralytics if missing from requirements
RUN pip install ultralytics

COPY . .

# Expose port (Render uses PORT env var)
EXPOSE 8000

CMD ["python", "main.py"]
