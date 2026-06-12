---
title: "Fresh install of Ubuntu 18.04 server, how is it doing mdns by default?"
date: 2020-01-12
forum: Networking &amp; Wireless
---

### Post by nabla on 2020-01-12
Hi, Just migrated a server to Ubuntu server (no gui), I've only configured wifi using netplan. I was surprised to see I can ssh and ping from another machine on my local network using hostname.lan even though I don't believe there is any mDNS casting configured out of the box. I see avahi is not installed and it appears systemd-resolved does not have mDNS enabled. 

I connected a laptop with Ubuntu 18.04 Desktop and I could connect to it with both hostname.lan and hostname.local, I assume .local is avahi.

I'm really curious as to how this is working. Thanks.

UPDATE: Nevermind, I believe this is a local DNS feature in my wireless router, for some reason this wasn't working with Debian before and had to use Avahi.

---

