---
title: "Wireless trouble in Ubuntu Server 7.10"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Arnitak on 2007-11-04
I installed ndiswrapper, the card works fine, however there is one problem. In the standard desktop installation I needed to change the domain name to that of my lan which is WORKGROUP. I did that using the GUI. How do I do it without the GUI in the CLI?

---

### Post by SpiritIsReality on 2007-11-04
howdy
any help here?
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
see heading "At Home"  a little under 1/2 way down page.
trails

[https://help.ubuntu.com/7.04/server/C/network-configuration.html](https://help.ubuntu.com/7.04/server/C/network-configuration.html)
I'm wondering if in the /etc/resolv.conf that WORKGROUP would work? Worth a try?
example:
search WORKGROUP
nameserver 192.168.0.1 or whatever the gateway is.

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/7.04/advanced-topics/C/index.html](https://help.ubuntu.com/7.04/advanced-topics/C/index.html)

---

