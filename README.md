# Docker Compose Traefik Example / Boilerplate
Berikut ini contoh / boilerplate docker-compose untuk traefik webserver

## How to use

Create docker network for traefik reverse proxy
```
docker network create traefik
```

Replace all example domain on docker-compose.yml and traefik.toml (put your email also for lets encrypt info)

then docker-compose up

next...

attach this on your docker-compose.yml apps
```
    networks:
      - traefiknet
    labels:
      - "traefik.enable=true"
      - "traefik.frontend.rule=Host:traefik.yourdomain.com"  # your apps domain
      - "traefik.port=8080" # change port that your apps use
      - "traefik.protocol=http"
      - "traefik.docker.network=traefiknet"
networks:
  traefiknet:
    external: true
```

then docker-compose up, your up should be serve on 443 (https), goodluck!

if you facing any issues, feel free to open issue on this repo. thanks.

Regards,  
Luqmanul Hakim
