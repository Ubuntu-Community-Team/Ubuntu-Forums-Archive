---
title: "USB D-Link Wireless Adapter Drivers"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by Thetri on 2015-10-27
I have a Laptop where the wireless card has went and my only choice for Wifi access is to use D-Link USB adapter. Only problem I'm having is I cannot find drivers for it to work in Ubuntu. So far I've tried Ubuntu, Xubuntu, Ubuntu MATE, Linux Mint, and Kubuntu all 14.04 versions. I haven't tried 15.04 or 15.10 and I prefer to stay away from non LTS releases if I can. 

The device is a D-Link AC Dual Band USB Adapter or a DWA-171 and it comes with a CD with the windows drivers. Is there a way to set this up to work on Ubuntu? Would installing the drivers through Wine work or is there a way to get it to work using some Linux packages? I tried googling it and it led me to a forum post of someone asking the same thing as me but no one answered it.

---

### Post by chili555 on 2015-10-27
Several USB wireless devices are made, over the product life cycle, with differing chipsets. Please open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Once we know your exact device, we'll proceed.

---

### Post by Thetri on 2015-10-27
```
Bus 001 Device 005: ID 2001:3314 D-Link Corp.
```

---

### Post by chili555 on 2015-10-27
Here ya go! [http://ubuntuforums.org/showthread.php?t=2168426](http://ubuntuforums.org/showthread.php?t=2168426)

---

### Post by Thetri on 2015-10-28
> **chili555 said:**
> Here ya go! [http://ubuntuforums.org/showthread.php?t=2168426](http://ubuntuforums.org/showthread.php?t=2168426)

Thanks this worked!

---

