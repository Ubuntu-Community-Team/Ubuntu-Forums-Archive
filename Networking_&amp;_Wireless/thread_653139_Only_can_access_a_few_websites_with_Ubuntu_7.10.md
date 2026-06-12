---
title: "Only can access a few websites with Ubuntu 7.10"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by bandido71 on 2007-12-29
I am new to Ubuntu. I installed ubuntu 7.10 AMD64 and i have problems contecting to internet, only can access this sites [www.google.cl](www.google.cl), [www.ibm.com](www.ibm.com), movistar.cl.
In firefox when i type other url, it keeps saying "Waiting for website...."
I am usin a wired Adsl conection. In windows xp i have no problems accessing the net. Also tried this and nothing happens :(

In Firefox:
about:config
network.dns.disableIPv6 true

and

sudo gedit /etc/modprobe.d/aliases

alias net-pf-10 ipv6 off
alias net-pf-10 off

---

### Post by bwtranch on 2007-12-29
Firefox blocks ads and pop-ups. Try turning off the pop-up blocker.

---

