---
title: "multiple identical network cards"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by merkur2k on 2006-10-03
I have setup a machine with ubuntu server that has 2 identical rtl8139 based pci cards in it. the first one works great, but I am having problems getting the second one to work.
when I try to configure/view it:
```
# ifconfig eth1
eth1: error fetching interface information: Device not found
```
yet it sees both of them:
```
# dmesg | grep eth
[42949395.670000] eth0: RealTek RTL8139 at 0xd0970800, 00:e0:29:72:8d:3e, IRQ 11
[42949395.670000] eth0:  Identified 8139 chip type 'RTL-8139B'
[42949395.680000] eth1: RealTek RTL8139 at 0xd0a4ac00, 00:e0:29:63:56:6b, IRQ 10
[42949395.680000] eth1:  Identified 8139 chip type 'RTL-8139B'
[42949397.110000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[42949427.150000] eth0: no IPv6 routers present
```
any ideas?

---

### Post by keithjr on 2006-10-03
Is it safe to assume that there is something plugged in to the eth1 card?

---

### Post by merkur2k on 2006-10-10
Yes, there is a cable plugged into the second card and it has a link.

---

