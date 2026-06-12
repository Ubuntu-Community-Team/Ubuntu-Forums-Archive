---
title: "Issues with eth0, udev and cloning"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by dschep on 2007-07-10
When I cloned a machine with an image I made of Ubuntu 7.04 from an other computer the network interface gets called eth1 (as opposed to eth0). When I did the same thing with a Debian system the solution was to edit the udev config file at /etc/udev/rules.d/70-persistent-net.rules and the issue would be resolved. For some reason this file doesn't exist in /etc/udev/rules.d on the Ubuntu system I just tried to clone so I was wondering what the solution to this problem would be in Ubuntu.

thanks in advance
dschep

EDIT: It seems Ubuntu 7.04 (fixed in gusty) uses /etc/iftab to name network interfaces which is deprecated, as opposed to letting udev handle it. I guess I'll check into that tomorrow.

EDIT2: Yup, editing /etc/iftab fixed the problem

(shouldn't have even bothered with this post apparently)

---

