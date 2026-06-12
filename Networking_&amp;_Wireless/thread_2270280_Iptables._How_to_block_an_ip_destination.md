---
title: "Iptables. How to block an ip destination"
date: 2015-03-21
forum: Networking &amp; Wireless
---

### Post by gabriel40 on 2015-03-21
Hello!!

is it possible to block packages that are being sending outside to a particular ip destination? I mean using iptables.

Thanks!!

---

### Post by gabriel40 on 2015-03-21
I found the solution. 

iptables -A OUTPUT -j DROP -d w.x.y.z

---

