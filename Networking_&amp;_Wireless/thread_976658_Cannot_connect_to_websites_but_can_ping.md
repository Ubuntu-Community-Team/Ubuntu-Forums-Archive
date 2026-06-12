---
title: "Cannot connect to websites but can ping"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by htmlland on 2008-11-09
Hello all,

On my ubuntu server I have found a strange problem which is preventing me from using apt-get and wget etc..

I can ping google.com and other domain names and other IP addresses but I cannot connect to the internet using apt-get or wget. I use this server as  DHCP, DNS and router for my internal home network and the other computers inside the network can connect fine with no problems; it seems to be a purly local issue!

Any ideas really appreciated and I can provide you with the contents of any config files needed.

Michael

---

### Post by Iowan on 2008-11-09
I'm not at all familiar with firewall rules, but (if you have firewall enabled) you might see if there's a rule that blocks traffic from server to internet.

---

### Post by htmlland on 2008-11-09
That was one of the first things iI though of too but it was set to all local network traffic to always allow and all localhost traffic to allow so it does not seem that that could be it :(

---

### Post by htmlland on 2008-11-17
Found the probem by mistake really! I was looking through my webmin bootup and shutdown init.d config thing and noticed there was a line not enabled for startup the loopback network device which

> Brings up the loopback (127.0.0.1) network device so that DHCP and other such things will work

This only effected me after a reboot (the first ever reboot) as it wassnt loaded up when it came live again.

A simple /etc/init.d/loopback start fixed the problem and now its also enabled on startup!

---

### Post by E-Cecilia on 2008-11-17
> **htmlland said:**
> Found the probem by mistake really! I was looking through my webmin bootup and shutdown init.d config thing and noticed there was a line not enabled for startup the loopback network device which



This only effected me after a reboot (the first ever reboot) as it wassnt loaded up when it came live again.

A simple /etc/init.d/loopback start fixed the problem and now its also enabled on startup!

OK but would you mind explaining what is it you did?

---

