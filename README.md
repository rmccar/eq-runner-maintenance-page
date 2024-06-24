# eq-runner-maintenance-page
This repo provides a static maintenance page for the EQ Questionnaire Runner application.

The page at `static-html/service.html` is intended to be served to users when the Runner application is unavailable.

This repo is not responsible for the provisioning or deployment of the page.

## Web server
While the `service.html` maintenance page can be deployed directly to a backend location (to be served from there by a CDN for example) this repo also provides an [Nginx](https://nginx.org/) web server Docker container, with a basic configuration to return the maintenance page for all requests it serves. The container can be deployed to a run time replacing the EQ Runner application.

## Build image locally
```
docker build -t runner-maintenance-page .
```

## Run container locallyfsddsf
```
docker run -it --rm -d -p 5000:5000 --name runner-maintenance-page runner-maintenance-page
```

Requested routes at `http://localhost:5000/` will be served with the maintenance page.

The route at `http://localhost:5000/status` will return an appropriate status response intending to serve as an indication that the Runner application is unavailable on that URL.

```
docker stop runner-maintenance-page
```