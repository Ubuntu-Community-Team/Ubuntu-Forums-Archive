---
title: "Cannot ping external IP"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Edo Monticelli on 2008-03-18
Hi all,
My pc is connected with a wired conncetion to a switch. I can ping gateway (192.168.1.254) and others pc on the lan, but cannot ping external (even numeric IP).
The connection is working on the other PC. 
I use static IP.
route -n shows :

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0    0        0 eth0
```


The ethernet interface get an IP address (192.168.1.24) but anyway I can't surf the net :(

Do you have any suggestion?

---

### Post by Edo Monticelli on 2008-03-18
Sorry,
it was a provider problem,
I used IP address 192.168.1.23 but my provider enabled only from 192.168.1.1 to 192.168.1.10
I always used a router...sorry

---

