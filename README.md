# Invenio Dev Containers

An example of using [Development Containers](https://containers.dev) to run Invenio RDM

## Why?

Invenio RDM can currently be run in one of two different modes for local development:

- Service Mode: Run services (search, db, cache, mq, etc.) in Docker and the application locally
- Container Mode: Run everything in a Docker container

Service Mode is currently difficult to achieve on macOS due to [the inability to install libxmlsec1](https://github.com/xmlsec/python-xmlsec/issues/163).

And Container Mode has a very slow development cycle since you need to rebuild the image after any changes.

Development Containers is a combination of both worlds - your development environment runs in a Docker container and the services run inside a Docker container in that container. You are essentially using Service Mode inside a Docker container, which gets you around the libxmlsec1 issues on macOS.

## How?

1. Clone this repo
1. Change into the repo directory
1. Start up Visual Studio Code or PyCharm
1. Your IDE will recognize that `.devcontainer` folder and offer to "open the project in a container". Say yes to this. 
1. Wait for the Docker image to build and start up
1. Once the image has started up, start up a new Terminal within Visual Studio Code or PyCharm
1. Start the services with `invenio-cli services setup -N`
1. Start the application with `invenio-cli run`
1. Visit the running application at <https://127.0.0.1:5000>

In order to create an admin account, run the following command:

```bash
pipenv run invenio users create username@example.com --password password --active --confirm
```
