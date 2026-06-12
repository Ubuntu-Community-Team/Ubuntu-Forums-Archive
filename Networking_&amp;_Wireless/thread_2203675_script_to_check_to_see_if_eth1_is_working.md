---
title: "script to check to see if eth1 is working"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by jrs2 on 2014-02-04
I'm using an external USB to ethernet dongle as eth1 on Ubuntu 11.10. There are times when eth1 will disappear, and a reboot or sudo ifup eth1 from terminal will fix the issue. I'm really new to Linux, but I'm assuming there would be a way to make a script that will do this automatically, I'm just not sure how or where to start. 

Say, every 5 minutes check to see if eth1 is active, if so do nothing, if not, do ifup eth1? Any help will be greatly appreciated.

---

### Post by brokenhachi on 2014-02-04
Maybe we should address the original problem that the eth interface is detaching.. can you post the output of dmesg?

---

