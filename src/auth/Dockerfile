# base image in python
# build our app on top of that image 
FROM python:3.10-slim-bullseye

RUN apt-get update \
  && apt-get install -y --no-install-recommends --no-install-suggests \
  build-essential default-libmysqlclient-dev \
  && pip install --no-cache-dir --upgrade pip
# set up workdir
WORKDIR /app
# set up requirements in a seperated layer -> if something changes, we dont need to rebuild every layer after it.
# build speed in CI/CD pipelines is essential
COPY ./requirements.txt /app
RUN pip install --no-cache-dir --requirement /app/requirements.txt
COPY . /app
# app running on port 5000
EXPOSE 5000
# run python3 server.py
CMD ["python3", "server.py"]

