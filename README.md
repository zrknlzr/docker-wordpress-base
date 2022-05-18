# docker-compose-wordpress

A simple Docker Compose workflow that sets up a LEMP network of containers for local WordPress development. Please follow all steps to get up and running. Some instructions might be specific to Linux.

## Setup

To get started, make sure you have [Docker](https://docs.docker.com/get-docker/) on your system, and then clone this repository.

Add your local testing domain to your hostfile and update `replace-me.test` in the nginx config.

Download the latest version of Wordpress in this directory with `wget https://wordpress.org/latest.zip && unzip -q latest.zip && rm -f latest.zip`

Add local certificates using [mkcert](https://github.com/FiloSottile/mkcert) by running `mkcert domain.tld` in the directory `/nginx/certs/`.

Next, navigate in your terminal to the directory you cloned this, and spin up the containers for the web server by running `docker-compose up -d --build site`.

Bringing up the Docker Compose network with `site` instead of just using `up`, ensures that only our site's containers are brought up at the start, instead of all of the command containers as well. The following are built for our web server, with their exposed ports detailed:

- **nginx** - `:80`
- **mysql** - `:3306`
- **php** - `:9000`

An additional container is included that lets you use the wp-cli app without having to install it on your local machine. Use the following command examples from your project root, modifying them to fit your particular use case.

- `docker-compose run --rm wp user list`

## ToDo

- [ ] Add script to get content/database from staging/live instance
- [ ] Add script to sync theme to staging/live instance