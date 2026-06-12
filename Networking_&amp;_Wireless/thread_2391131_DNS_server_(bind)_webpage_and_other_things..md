---
title: "DNS server (bind) webpage and other things."
date: 2018-05-06
forum: Networking &amp; Wireless
---

### Post by kakefett on 2018-05-06
I have a webpage that I redirect to my public IP-adress,
Thats ok.
But I wonder should I run DNS server in this case? If you go to my webpage blablabla.com you will come to my page anyway, so what do DNS server do in this situasion?

---

### Post by TheFu on 2018-05-06
You shouldn't run DNS without need.  I've been hacked a few times, 1 time it was through bind/DNS.  DNS is a highly attacked vector for bad guys.

Definitely don't run a public facing DNS without very careful thought. Be certain to read a few "best practices" articles before doing it. DNS is a cornerstone for network security.  Losing control of your DNS can allow someone else to totally pwn your network. Totally, completely, even certs.

Running an internal DNS isn't nearly as dangerous and can help network management be cleaner.

---

