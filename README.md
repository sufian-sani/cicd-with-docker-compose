# How to run app with Docker-compose

## Install docker compose latest version
    DOCKER_COMPOSE_VERSION=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)

    sudo curl -L "https://github.com/docker/compose/releases/download/$DOCKER_COMPOSE_VERSION/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

* $(uname -s) → OS (Linux/macOS)

* $(uname -m) → Architecture (x86_64/arm64)

## Make it executable
sudo chmod +x /usr/local/bin/docker-compose

## Verify installation

    docker compose version

* You should see like: docker compose version 2.x.x

## Build and run 2 container (mysql & flask app)

    docker compose  up -d (for the first time with for single file: ie. compose.yaml)

    docker compose -f docker-compose.yml up -d (if you have to compose files, i.e. compose.yaml, docker-compose.yaml)

    docker compose up --build -d (if you make changes to the app, re-build and run)

## Stop and remove everything that was created by docker compose up, including: Containers, Networks (created by Compose), Images (optional, with a flag), Default anonymous volumes (optional, with a flag)

    docker compose down --volumes --rmi all
