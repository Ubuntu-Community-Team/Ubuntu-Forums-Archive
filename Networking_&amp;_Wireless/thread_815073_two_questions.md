---
title: "two questions?"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by menschtx on 2008-06-01
How to ping and is there an equivelent for ctrl+alt+delete?

---

### Post by bwhite82 on 2008-06-01
You can ping in a terminal with:

ping ip.ad.dr.es.s

or open System>Admin>Network Tools

CTRL+ALT+DEL equivalent is:

System>Admin>System Monitor

---

### Post by chili555 on 2008-06-01
To make ping a bit more manageable, specify the count, or number of pings to send. I use three, because it's quick, and if pings won't get there in three, they won't get there in 156!```
chili@LAPTOP60:~/Desktop$ ping -c3 www.google.com
PING www.l.google.com (74.125.47.103) 56(84) bytes of data.
64 bytes from yw-in-f103.google.com (74.125.47.103): icmp_seq=1 ttl=242 time=20.9 ms
64 bytes from yw-in-f103.google.com (74.125.47.103): icmp_seq=2 ttl=242 time=21.0 ms
64 bytes from yw-in-f103.google.com (74.125.47.103): icmp_seq=3 ttl=242 time=21.3 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 20.930/21.120/21.364/0.181 ms
```

---

