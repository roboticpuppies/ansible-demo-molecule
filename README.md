# Testing Ansible Role with Molecule and Docker.

## About this repository

This is a example repository that demonstrate on how to test an ansible role using Molecule and Docker. This role only contains simple tasks to install an NGINX web server and change the content of the default index.html file. The html content in each OS distribution will be different by outputing the distribution name and version. I'll test this role to RockyLinux and Debian 12.

## Molecule configuration

In this demo I'll focus on 2 files: `converge.yml` and `molecule.yml`. If you need more customization, read the [official documentation](https://ansible.readthedocs.io/projects/molecule/getting-started/).

Molecule will create two instances:
- Debian 12:
  - Exposing port 8080
  - Using docker image from `geerlingguy/docker-debian12-ansible:latest`
- Debian 12:
  - Exposing port 8080
  - Using docker image from `geerlingguy/docker-rockylinux9-ansible:latest`

See [molecule/default/molecule.yml](./molecule/default/molecule.yml) for the details.

## Expected output

When you run `molecule converge` you can access the container through these ports:
- Rocky:
  - It will show this text: `NGINX is running on Rocky 9.5 (Blue Onyx)`
- Debian:
  - It will show this text: `NGINX is running on Debian 12.8 (bookworm)`

## Credits

Thank you [geerlingguy](https://github.com/geerlingguy/) for writing a amazing book and providing the docker images needed to use with Molecule.