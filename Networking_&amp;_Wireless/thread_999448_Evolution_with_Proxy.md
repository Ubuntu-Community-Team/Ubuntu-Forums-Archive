---
title: "Evolution with Proxy"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by irishdunn on 2008-12-01
I am using Evolution on my laptop. I travel quite a bit and want to push all traffic through my dedicated server using a socks proxy.

I use this command to create the proxy:
ssh -D 127.0.0.1:8080 -fN user@server

Evolution doesnt seem to be 'respecting' my Gnome proxy settings, it will connect to my email accouns 'IMAP gmail' with or without me creating the proxy.

I would like evolution to use the socks proxy for all traffic.

---

### Post by steak on 2008-12-02
You should find that there is proxy settings in the preferences of evolution.

Good luck :)

---

