# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.177.0/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version: bionic, focal
ARG VARIANT="focal"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# Change shell to Zsh.
ENV SHELL /bin/zsh

# Prerequisites for apt-get install.
RUN curl -fsSL https://deb.nodesource.com/setup_14.x | bash -
RUN curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
RUN echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | \
    tee /etc/apt/sources.list.d/kubernetes.list

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    vim \
    tree \
    make \
    python3-pip \
    nodejs \
    docker.io \
    kubectl

# Add vscode user to docker group.
RUN usermod -aG docker vscode

# Install Poetry.
USER vscode
RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3 -
