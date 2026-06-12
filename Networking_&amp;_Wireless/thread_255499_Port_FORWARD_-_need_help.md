---
title: "Port FORWARD - need help"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by cdc on 2006-09-11
Hi!

I tried all the methods I could find, but no success, ex:

iptables -t nat -A PREROUTING -p tcp -d 82.174.133.216 --dport 1723 -j DNAT --to-destination 192.168.0.200

My ubuntu has a ppp0 and an eth0, the pp0 connects to internet, and the eth0 to the LAN. I've installed the dhcpd for automatic NAT.

I don't know what is wrong ](*,) , please help!

Thanks!

---

