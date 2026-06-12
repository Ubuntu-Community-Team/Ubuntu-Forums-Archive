---
title: "Multiple DSL routers"
date: 2005-08-29
forum: Networking &amp; Wireless
---

### Post by nverhaar on 2005-08-29
Hey guys,

I have Ubuntu installed as SERVER mode, with eth0 connected to the local network and eth1 connected to a DSL modem. This works PERFECTLY, however now I wish to add several more DSL modems as eth2, eth3, eth4, etc to provide VPN connections for remote offices.

My problem is, all incoming data comes in on the appropriate interfaces, however outgoing packets appear to all go out via eth1 (the default route). This means if anyone pings or connects or does anything on ANY of the modems, all replies go back out via ETH1 rather than the interface they came in on.

On an older Mandrake server I ran the following to correct the problem, however when I run the same commands on Ubuntu it seems to kill all network activity.

ip rule add from 111.222.333.111 dev lo table 57 prio 1500
ip rule add from 111.222.333.211 dev lo table 58 prio 1501
ip rule add from 111.222.333.311 dev lo table 59 prio 1502
ip rule add from 111.222.333.411 dev lo table 60 prio 1503
ip route add default via 111.222.333.110 table 57 src 111.222.333.111
ip route add default via 111.222.333.210 table 58 src 111.222.333.211
ip route add default via 111.222.333.310 table 59 src 111.222.333.311
ip route add default via 111.222.333.410 table 60 src 111.222.333.411

ANY IDEAS?!?

---

### Post by nverhaar on 2005-08-30
Nobody ever answers my posts!!

I think I might cry myself to sleep!

 :cry:  :cry:  :cry:  :cry:  :cry:

---

