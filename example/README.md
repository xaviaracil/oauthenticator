# OAuthenticator

Example of running [JupyterHub](https://github.com/jupyterhub/jupyterhub)
with [GitLab OAuth](http://docs.gitlab.com/ce/api/README.html) for authentication.

## setup

Edit the file called `userlist` to include one GitLab user name per line.
If that user should be an admin (you!), add `admin` after a space.

For example:

```
mal admin
zoe admin
wash
inara admin
kaylee
jayne
simon
river
```

## build

Build the container with:

    docker build -t jupyterhub-oauth .

### ssl

To run the server on HTTPS, put your ssl key and cert in ssl/ssl.key and
ssl/ssl.cert.

## run

Add your host (if you have a on-premise GitLab installation), oauth client id, client secret, and callback URL to the `env file`.
Once you have built the container, you can run it with:

    docker run -it -p 8000:8000 --env-file=env jupyterhub-oauth

Which will run the Jupyter server.
