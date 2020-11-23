FROM python:3.9-alpine

WORKDIR /code

RUN apk add build-base postgresql-dev && pip install gunicorn
COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD sleep 10 && cd backend && python manage.py migrate && \
    gunicorn --bind 0.0.0.0:8000 backend.wsgi