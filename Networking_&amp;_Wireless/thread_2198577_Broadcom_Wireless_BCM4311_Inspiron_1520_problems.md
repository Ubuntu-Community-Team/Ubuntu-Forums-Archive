---
title: "Broadcom Wireless BCM4311 Inspiron 1520 problems"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by prodigalson7777 on 2014-01-09
I have been trying for quite some time now to get my wireless working with Ubuntu 13.04.  I am a beginner and have tried finding the solution to no avail.  The most comprehensive thread i have found so far is [http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx) but nothing has worked.  I could really use someones help walking me through the solution.

---

### Post by chili555 on 2014-01-09
Please get a temporary wired ethernet connection. Open a terminal and do:```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and tell us if it's working perfectly.

---

### Post by prodigalson7777 on 2014-01-11
As indicated, Success!!!!  Thanks so much for your help.

---

### Post by chili555 on 2014-01-11
Awesome! Glad it's working. Have fun!

---

