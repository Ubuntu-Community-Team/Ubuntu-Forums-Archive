---
title: "can't deploy caddy on portainter"
date: 2022-09-16
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-09-16
[SIZE=2][FONT=arial]when i try to run caddy image in portainer [https://hub.docker.com/_/caddy](https://hub.docker.com/_/caddy)
it shows[COLOR=#667085]
[/COLOR]```
failed to deploy a stack: Network caddy_default Creating Network caddy_default Created Container caddy-caddy-1 Creating Container caddy-caddy-1 Created Container caddy-caddy-1 Starting Error response from daemon: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container process: error during container init: error mounting "/Caddyfile" to rootfs at "/etc/caddy/Caddyfile": mount /Caddyfile:/etc/caddy/Caddyfile (via /proc/self/fd/6), flags: 0x5000: not a directory: unknown: Are you trying to mount a directory onto a file (or vice-versa)? Check if the specified host path exists and is the expected type
```
how do i create caddyfile on portainer ??[/FONT][/SIZE]

---

