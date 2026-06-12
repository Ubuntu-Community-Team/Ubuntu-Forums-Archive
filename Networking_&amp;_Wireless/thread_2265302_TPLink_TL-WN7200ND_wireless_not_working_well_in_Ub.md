---
title: "TPLink TL-WN7200ND wireless not working well in Ubuntu 14.04"
date: 2015-02-14
forum: Networking &amp; Wireless
---

### Post by Walter2014 on 2015-02-14
Hi,

I have a tp-link wireless usb TL-WN7200ND. I just tested out the speed of my connection on Speedtest.net and it only shows up to half of my speed. I tried testing the speed in Windows 7 and its working like it should. This tells me that this is an issue with Ubuntu and this specific wireless device. Any solutions on how it get it working properly in Ubuntu? 

Thanks!!

---

### Post by SeijiSensei on 2015-02-14
I just bought a new computer and am using a TP-Link USB device as well.  I hadn't noticed the difference in speed between Windows and Linux because I'm on a fast connection from Verizon FiOS. After reading your posting, I ran a test at speedtest.net and found to my surprise that my speeds were also about half what I was getting in Windows.  After a little Google searching I found [this article](http://www.htpcbeginner.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/) which suggests creating (as root with sudo) a file called /etc/modprobe.d/ath9k.conf containing the line:
```
options ath9k nohwcrypt=1
```
and rebooting.  (That passes the nohwcrypt option to the Atheros ath9k driver at boot.)  My speeds are now close to what I saw in Windows.

---

### Post by Walter2014 on 2015-02-14
I tried it but it hasnt changed my speeds unfortunately. Any other ideas?

---

