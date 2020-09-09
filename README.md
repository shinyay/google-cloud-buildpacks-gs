# Spring Music Container

Containerized Spring Music Application

## Description
This is a Spring Music Application containerized with Distroless Java Runtime.

- [spring-music-container:latest](https://hub.docker.com/repository/docker/shinyay/spring-music-container)

## Demo

### Local Container Build & Run
#### 1. Build Container Image
```
$ docker build -t shinyay/spring-app .
```

#### 2. Run Container App
```shell script
$ docker run --rm -d -p 8080:8080 --name spring-app shinyay/spring-app
```

### Build on Cloud Build
#### (Option) Register SSH Key
- Cloud Source Repositories
  - Manage SSH Keys
    - Register SSH Key

![register-ssh](https://user-images.githubusercontent.com/3072734/92601920-5f188b80-f2e8-11ea-8566-5f5e40d6d66f.png)

#### Create Source Repository
```
$ gcloud source repos create spring-app-repo
```

```
$ gcloud source repos list
REPO_NAME        PROJECT_ID                   URL
spring-app-repo  shinyay-build-999999-000000  https://source.developers.google.com/p/shinyay-build-999999-000000/r/spring-app-repo
```

#### Add Remote Repository
```
$ git remote add google ssh://<USER_ID>@source.developers.google.com:2022/p/shinyay-works-999999-000000/r/spring-app-repo
```

#### Create Trigger for Building app
```
$ gcloud beta builds triggers create cloud-source-repositories \
    --repo=spring-app-repo \
    --branch-pattern=".*" \
    --build-config=cloudbuild.yaml
```

```
$ gcloud beta builds triggers list
```

#### Run Trigger
Edit some source code and commit & push.

- [Cloud Build Dashboard](https://console.cloud.google.com/cloud-build)

#### (Option) Run Trigger by manual
```
$ gcloud beta builds triggers run <TRIGGER_NAME> --branch master
```

## Features

- Distroless Java
- Multi-stage Build

## Requirement

## Usage

## Installation

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/34c6fdd50d54aa8e23560c296424aeb61599aa71/LICENSE)

## Author

[shinyay](https://github.com/shinyay)
