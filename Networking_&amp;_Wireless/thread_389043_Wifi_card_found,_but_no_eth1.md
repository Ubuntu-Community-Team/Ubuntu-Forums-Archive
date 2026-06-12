---
title: "Wifi card found, but no eth1"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by moongo0se on 2007-03-20
Heya all. Just did a kernel update on my Xubuntu 6.10.
After that, my wireless card was *gone*. I did a lspci, and found it there, then a modprobe ipw2200, which worked, but there is still no eth1. So, what to do now?

---

### Post by spd106 on 2007-03-21
Try this```
sudo lshw -class network
``` It will tell you the interface name and which driver is controlling the interface.

---

