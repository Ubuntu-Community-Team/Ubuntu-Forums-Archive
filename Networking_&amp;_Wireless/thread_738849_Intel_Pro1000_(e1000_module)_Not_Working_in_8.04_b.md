---
title: "Intel Pro/1000 (e1000 module) Not Working in 8.04 beta"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by keirgordon on 2008-03-29
Have an intel pro/1000 network card.  From an 8.04  (AMD64) live cd, the e1000 module is loaded and card detected. 

* I have a link light, but ethtool says no link detected.
* dhcp can't get any response
* I can set a static ip, but can't ping anything
* A different, 100mb card, worked successfully.

Tried rebooting many times of course, taking eth0 up and down, restarting networking, modprobe e1000.

dmesg doesn't show anything interesting other than success loading e1000.

Any ideas?

---

