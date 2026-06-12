---
title: "How To Find A Wireless Connection"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by techgeek40 on 2007-12-14
I have a Netgear 54 Mbps Wireless PC Card (PCMCIA)
WG511 v2

How do I find a wireless connection that is in my area?

---

### Post by chili555 on 2007-12-14
Assuming your wireless interface is eth1, try:```
sudo iwlist eth1 scan
```It may take a few tries.

---

