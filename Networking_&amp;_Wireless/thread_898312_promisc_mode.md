---
title: "promisc mode"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by sulekha on 2008-08-23
Hi,

i typed man ifconfig in my terminal to get the following

-promisc
 
Enable or disable the promiscuous mode of the interface.  If selected, all packets on the network  will  be received by the interface.

i have also read that promiscuous mode is enabled only for certain troubleshooting situations/applications.

can any one give the situations where promiscuous mode is enabled ?

---

### Post by mellowd on 2008-08-23
promiscuous mode is where your network cards captures all packets, regardless of whether it was addressed to it or not. This can help with troubleshooting.

It can also be used to sniff out passwords and the like!


Generally you don't need it. For normal day to day use it isn't required.

---

