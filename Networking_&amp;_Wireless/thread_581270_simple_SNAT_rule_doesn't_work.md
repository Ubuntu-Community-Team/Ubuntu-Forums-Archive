---
title: "simple SNAT rule doesn't work?"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by pismikrop on 2007-10-19
Hi:

these are the commans that i used for simple SNAT:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -p tcp -o eth0 -j SNAT --to 192.168.1.10

but it doesn't work.

i have to add a DNAT rule.

---

### Post by pismikrop on 2007-10-19
any idea?

---

