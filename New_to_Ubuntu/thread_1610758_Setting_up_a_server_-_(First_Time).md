---
title: "Setting up a server - (First Time)"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Verbeck on 2010-11-01
i've installed LAMP on my desktop and i'd like to open up the box to the world

so, i followed the port forward instructions for HTTP @ [portforward.com]("http://portforward.com/english/routers/port_forwarding/UTStarcom/UT-300R/HTTP.htm") for my ancient router (utstar UT-300R).
but i type the public ip of the system in a brower, it redirects to the router's settings page 192.168.1.1. however its available through the local ip.(192.168.1.2)

so what am i doing wrong?:confused::confused:

__
btw [http://canyouseeme.org/](http://canyouseeme.org/) and the port scanner in network tools  says the port 80 is open :confused:

---

### Post by peculiar penguin on 2010-11-01
Your router probably doesn't support [NAT loopback]("http://www.dyndns.com/support/kb/loopback_connections.html").

---

### Post by Verbeck on 2010-11-01
> **peculiar penguin said:**
> Your router probably doesn't support [NAT loopback]("http://www.dyndns.com/support/kb/loopback_connections.html").
that link gave me an idea, so i requested some shots from [http://browsershots.org/](http://browsershots.org/).
seems like others can view it through the public ip. THANX :D\\:D/

---

