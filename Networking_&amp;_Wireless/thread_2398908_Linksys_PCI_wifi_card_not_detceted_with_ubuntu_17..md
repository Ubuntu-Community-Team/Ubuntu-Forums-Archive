---
title: "Linksys PCI wifi card not detceted with ubuntu 17.10"
date: 2018-08-19
forum: Networking &amp; Wireless
---

### Post by francois_baret on 2018-08-19
I attached my wireless-info.txt file which has been successfully uploaded with pastebin at :[http://paste.ubuntu.com/p/gsrtwZXHtg/](http://paste.ubuntu.com/p/gsrtwZXHtg/).
The PC on which this wifi adapter has been plugged in is connected through ethernet to a remote router.
I need this wifi adapter to create an access point (hotspot?) for the other devices located near the PC and not to connect to the wifi of the router which is anyway to far to be reached where the PC stands.
Thanks for your help!

---

### Post by chili555 on 2018-08-19
With a working internet connection, please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Reboot.

Ubuntu 17.10 reached End of Life on July 19, 2018. You are no longer receiving important security updates. Please upgrade soon.

---

