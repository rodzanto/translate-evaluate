FROM python:3.8-buster

RUN mkdir -p /srv/worker

COPY requirements.txt /srv/worker

WORKDIR /srv/worker

RUN pip install -r requirements.txt

ADD model /srv/worker/
COPY app.py   /srv/worker

RUN chmod +x /srv/worker/app.py

ENV WORKER_SQS_QUEUE_URL="https://sqs.eu-west-1.amazonaws.com/889960878219/translate-bert-input"
ENV BUCKET_NAME="rodzanto2021ml"
ENV PREFIX="translate/score/"

ENTRYPOINT ["/srv/worker/app.py"]
