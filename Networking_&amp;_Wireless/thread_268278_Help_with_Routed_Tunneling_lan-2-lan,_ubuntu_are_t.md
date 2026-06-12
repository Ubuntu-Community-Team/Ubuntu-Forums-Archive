---
title: "Help with Routed Tunneling lan-2-lan, ubuntu are the 2 gateways"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by heavyt on 2006-09-29
I am trying to set-up routed tunneling between 2 lan networks with each having ubuntu boxes as the hamachi connections. The two ubuntu boxes are behind routers.

In box 1 and 2 I added

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```.
 Yes eth0 are the local lan network cards.

But I can't ping any ip's on the local network not even the ubuntu boxes ip's (I can ping the hamachi ip's).

---

