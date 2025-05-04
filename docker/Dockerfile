FROM python:3.13-slim-bookworm

# install deps
RUN apt-get update && apt-get -y install \
    bash ffmpeg git

WORKDIR /rife
COPY requirements.txt .
RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

# setup RIFE
COPY . .
COPY --chmod=755 docker/inference_img docker/inference_video /usr/local/bin
COPY model/oldmodel/RIFE_HD.py model/oldmodel/RIFE_HDv2.py model/

# add pre-trained models
COPY train_log /rife/train_log

WORKDIR /host
ENTRYPOINT ["/bin/bash"]

ENV NVIDIA_DRIVER_CAPABILITIES=all
