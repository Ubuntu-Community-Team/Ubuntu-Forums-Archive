---
title: "zd1211 chipset - in case you can connect to wireless networks but do not obtain an IP"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by tompi on 2007-06-11
Hi,

I was able to see the wireless networks, and could use network manager to connect to a network. Sometimes I was able to obtain an IP and start surfing, sometime I did not receive an IP (it stayed at 0.0.0.0) - there seemed to be no logic involved

Following bug report put me in the right direction to solve it for me as there was a logic: When an external USB harddrive was connected at boot-up, i was able to use wireless, if not, it didn't work. Something to do with USBFS not being loaded by default. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/74362](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/74362)

Belkin wireless G USB network adaptor F5D7050 V4

hope this can help

---

