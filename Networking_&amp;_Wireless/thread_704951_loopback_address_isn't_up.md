---
title: "loopback address isn't up"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by loup on 2008-02-22
Hi

I am new to 7.1 and have the following problem.
My loopback address doesn't come up on start up any longer. I need to do a manual: sudo ifconfig lo up.

cat /etc/network/interfaces shows:
auto lo
iface lo inet loopback

auto eth0
gateway 192.168.1.1

How can I have the loopback to startup each time I switch on my PC?

---

