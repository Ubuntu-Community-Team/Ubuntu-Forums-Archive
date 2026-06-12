---
title: "dual wan pppoe loadbalance"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by atux on 2014-06-21
hello everyone.
in an ol pc that has 3 ethernet cards i am running ubuntu 10 server x86.
i do need to setup my 2 dsl providers to make use of both of the connections.
i do have the pppoe creentials from both of the providers.
the setup i woul like to make use of is:
eth0 ISP1
eth1 ISP2
eth2 LAN (192.168.50.0/24)

the modems are already in bridge mode and the subnets for the local management of the modems are
ISP1 192.168.1.0/24 the modem is on 192.168.1.1
ISP2 192.168.2.0/24 the modem is on 192.168.2.1

i would like to make use of both of the connections, but without the common issues of https, returning losses of packets.
is there a nice explanatory guide?

---

