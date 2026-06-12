---
title: "Ad-Hoc with Broadcom"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by yurr on 2008-05-21
Hi everyone,

a have a Dell Inspirion 1501 laptop with Broadcom BCM4311 wi-fi card runnung Ubuntu 8.04 Hardy

Of course, wi-fi does not work 'out of the box', but installing b43-fwcutter was enough for my computer to see the wi-fi networks and be able to connect.

Except one thing - Ad-Hoc networks. It sees them, when I try to connect I am prompted for password, but then nothin happens, i.e. I'm not connected. Setting mode to Ad-Hoc using command line does not help too.

I tried installing ndiswrapper with the GUI - it did not help (using drivers from Dell website), then tried to follow the instructions from [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)) - got stuck at the point of renaming eth1 to wlan0 in /etc/iftab - there is no such file under Hardy.

Any ideas how to make Ad-Hoc working?

---

