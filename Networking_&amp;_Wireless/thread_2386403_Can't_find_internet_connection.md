---
title: "Can't find internet connection"
date: 2018-03-05
forum: Networking &amp; Wireless
---

### Post by un1dade on 2018-03-05
Hi everyone,

I've recently installed Lubuntu Desktop 64-bit 16.04.3 LTS on my MacBook 3,1 (2007) but can't find Wi-Fi networks to connect to internet.
I've read several forum threads and articles but was unable to solve the problem.

This is my laptop: [https://everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.0-white-13-late-2007-santa-rosa-specs.html](https://everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.0-white-13-late-2007-santa-rosa-specs.html)
except it has 2 GB RAM instead of the original 1 GB.

And this is my Broadcom model: bcm4321 802.11a.

Please take into consideration that I don't have the possibility to connect my laptop to the internet through ethernet cable.

---

### Post by kc1di on 2018-03-05
According to broadcom the correct linux driver for your card is the bcmwl-kernel-source.  You will need at temporary ethernet connection to download and install it.
once your connected install with this command: ```
sudo apt install bcmwl-kernel-source
```
reboot and see if wireless works. good luck.

---

### Post by un1dade on 2018-03-07
Thank you for the reply. Is there any other way to fix this issue? Like I said, I don't have the possibility to connect myself through ethernet...

---

### Post by un1dade on 2018-03-08
Fixed the problem by installing Xubuntu!

---

