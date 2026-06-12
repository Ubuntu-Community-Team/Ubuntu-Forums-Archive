---
title: "cannot ping to localhost"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by ghmercado on 2007-05-30
i have to do this:

sudo ifconfig lo 127.0.0.1 up

everytime. please tell me How to configure my edgy to avoid having to do so? This has to do with getting mysql to run btw. Thanks in advance.

---

### Post by mbradlcu on 2007-05-31
what does your /etc/network/interfaces look like? here's mine:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp



---

