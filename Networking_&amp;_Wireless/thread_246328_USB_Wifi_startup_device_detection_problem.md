---
title: "USB Wifi startup device detection problem"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by JeBeKe on 2006-08-29
My ZD1211 device is not recognised during startup.
If I unplug it during startup, and plug it in after the pc is running, there is NO issue.
If it is plugged in during startup, then the device is not recognised, not even in the lsusb list.

Apparently, the device detection is already started before the
modules are loaded. (btw... the ZD1211 is in the /etc/modules).

How can I make sure the module is loaded BEFORE the device recognition is started?

There is a usb1-1 read error during startup, coming from the device.
Apparently, the device cannot be read. I think the zd1211 module
downloads the correct firmware, but as the detection is done
before the module is loaded, the reading fails.

I hope someone can help me out here.

---

