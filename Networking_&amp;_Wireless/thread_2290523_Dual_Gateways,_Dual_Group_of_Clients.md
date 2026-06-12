---
title: "Dual Gateways, Dual Group of Clients"
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by im4mqta on 2015-08-12
Currently, I'm running Ubuntu Server 12.04.4 LTS as a gateway router for internet cafe.

Network Conf:
ppp0 : 182.X.Y.Z (via DHCP on eth0)
ppp1 : 36.X.Y.Z (via 192.168.10.2 on eth1)
eth2 : 192.168.1.50 ( Internal LAN )

**Currently, all clients (192.168.1.1 - 192.168.1.20) can access to intenet through gateway ppp0 **:KS**. Gateway ppp1 used only as a backup****.**
This is what i'ld like to do:
- Request from Internal LAN Group A: 192.168.1.1-192.168.1.10 it should be use **ppp0** gateway.
- Request from internal LAN Group B: 192.168.1.11-192.168.1.20 it should be use **ppp1** gateway.


Is it possible to set route, iptables etc to work in this way? What is the best solution? :D

---

### Post by im4mqta on 2015-08-17
please Help me...  :???:

---

