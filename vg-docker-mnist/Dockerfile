# Start with a Linux micro-container to keep the image tiny
# FROM alpine:3.7
FROM ubuntu

# Document who is responsible for this image
MAINTAINER Seetharami R. Seelam "sseelam@nyu.edu"

# Install just the Python runtime (no dev)
RUN apt-get update && apt-get install -y \
    python3 python3-dev gcc gfortran musl-dev \
    python3-pip ca-certificates

# Set up a working folder and install the pre-reqs
WORKDIR /app
ADD mnist/requirements.txt /app
RUN pip3 install --upgrade pip setuptools 
RUN pip3 install -r requirements.txt
# RUN pip3 install torch
# RUN pip3 install torchvision
# RUN pip3 install torch===1.8.0+cpu torchvision===0.9.0+cpu -f https://download.pytorch.org/whl/torch_stable.html

# Add the code as the last Docker layer because it changes the most
ADD mnist/main.py  /app/main.py

# Run the service
WORKDIR /app
CMD [ "python3", "main.py", "--dry-run" ]

