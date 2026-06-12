---
title: "Cannot connect to network using Ethernet cable..."
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by jon80 on 2014-03-15
I tried checking whether my cable modem can provide Internet to my laptop which has a network card that had its hardware repaired (so I am not sure whether the technician seated the network card properly or not), but nevertheless, although the network configuration loads without any errors, I can only ping 127.0.0.1, but there is no Internet connection even though the cable modem provided by the ISP (Melita cable) seems to have DHCP configured as I can connect over WiFi from another laptop that has Win8.  I have not configured any settings manually as only VPN was available as an interface through the Networks dialog.

What do you think is the problem, is this a software bug or a hardware issue, or both?

---

### Post by The Cog on 2014-03-15
I would start off with the commands
```
lspci -v
ifconfig -l
```
to see what the OS thinks is there.
If you can post the results of those, it would be a good starting point.

---

