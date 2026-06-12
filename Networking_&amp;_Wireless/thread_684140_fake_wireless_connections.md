---
title: "fake wireless connections?"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by achortleaday on 2008-01-31
I am running Gutsy on my Dell Inspiron 1501. My wireless worked fine with my home network right out of the box once I installed the restricted broadcom driver. However, now that I am back at school it is having issues. It will see all of the networks in the area, and will say it's connected to my school's WPA2 Enterprise network. However, no programs will actually connect to the internet. I tried doing ndiswrapper about four different ways ... one of them let me connect for real, but then after about a minute or so nothing would work anymore, even though it would say I was still technically connected. What can I do??

---

### Post by kevdog on 2008-01-31
If you are assigned an ip address, its either a route(gateway) issue or dns issue.

Check the gateway with
route -n


Can you ping an outside IP address?  If you can, then its a DNS problem.

---

### Post by achortleaday on 2008-01-31
route -n gives me this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth1

---

