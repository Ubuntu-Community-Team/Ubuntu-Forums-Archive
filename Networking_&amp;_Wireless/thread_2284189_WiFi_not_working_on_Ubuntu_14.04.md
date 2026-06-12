---
title: "WiFi not working on Ubuntu 14.04"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by Superpuzzone on 2015-06-27
Hi, I have recently installed Ubuntu 14.04 on my Acer Extensa 5200 and everything works fine except for the wireless networking. I went to Settings/ Softwares and Updates/ Additional Drivers, and what I see is "Broadcom Corporation: BCM4311 802.11b/g WLAN" saying "this device is not working". I then switch from "do not use the device" to "using Broadcom 802.11 Linux STA wireless driver" and clicked on "Apply Changes". It starts applying the changes but then it randomly stops and switches automatically to the "do not use the device" option... can anybody help please? Thank you :D

---

### Post by wildmanne39 on 2015-06-27
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
then do:
```
sudo apt-get install firmware-b43-installer
```
Reboot and wireless should work.
Thanks

---

### Post by Superpuzzone on 2015-06-27
Perfect! It worked at first try! Thanks a lot again

---

### Post by wildmanne39 on 2015-06-27
Glad it worked!

---

