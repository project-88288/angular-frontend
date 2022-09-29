# syntax=docker/dockerfile:1.4

FROM node:16.17-alpine AS build 

RUN mkdir /project
WORKDIR /project

RUN npm install -g @angular/cli@14

COPY package.json package-lock.json ./
RUN npm ci

COPY . .

CMD ["ng", "serve", "--host", "0.0.0.0"]

FROM build as dev-envs

#RUN <<EOT
#apt-get update
#apt-get install -y --no-install-recommends git
#EOT

#RUN <<EOT
#useradd -s /bin/bash -m vscode
#groupadd docker
#usermod -aG docker vscode
#EOT

# install Docker tools (cli, buildx, compose)
COPY --from=gloursdocker/docker / /

CMD ["ng", "serve", "--host", "0.0.0.0"]
