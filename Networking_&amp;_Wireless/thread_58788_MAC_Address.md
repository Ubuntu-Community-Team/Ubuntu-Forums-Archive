---
title: "MAC Address"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by Qrk on 2005-08-21
When I first installed Ubuntu, my network card was connected fine, and I could get on the net. However, someone had the same MAC address and we couldn't be connected at the same time. So I attempted to change my MAC address with the command...

ifconfig eth0 hw ether 

which did change my MAC address just fine. But when I brough eth0 back up I couldn't connect. I'm fairly new at Linux and I can't seem to find out how to solve this problem. I tried reseting my MAC address to what it was before, but that didn't work. Could someone help me?

---

### Post by nad on 2005-08-21
I would suggest that you also reset your DHCP server/gateway or other hardware interface.
.

---

### Post by Qrk on 2005-08-21
Thanks. It worked like a charm.

---

