---
title: "ubuntu 18.04 fresh install, no wifi adapter"
date: 2018-08-15
forum: Networking &amp; Wireless
---

### Post by smedini on 2018-08-15
Please consider the following paste bin about my wifi config.
I have a wifi card, but ubuntu doesn't display it in the wifi menu

[https://pastebin.com/XkT7yjJR](https://pastebin.com/XkT7yjJR)

Thnaks you,
best regards

---

### Post by kc1di on 2018-08-15
First you need to go to software and upadates then the additonal drivers tab. and see if there are any recommended drivers for your card. Should be bcmwl-kernel-source for your card. Install the recommended driver and reboot. you will need to be connected via an Ethernet cable to do that.

If you want you can do the same thing in a terminal by installing the following. ```
sudo apt install bcmwl-kernel-source 
``` then reboot and wireless should be working.

---

### Post by praseodym on 2018-08-15
SecureBoot needs to be turned off, the driver is not signed

---

