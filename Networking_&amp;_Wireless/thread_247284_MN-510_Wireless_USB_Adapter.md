---
title: "MN-510 Wireless USB Adapter"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by Sketch on 2006-08-30
I am new to Linux...
I installed Windows XP on one drive
I installed Linux on another drive

After logging into windows the usb device was detected, installed, and I entered the WEP Key. The internet was then up and running

After logging into Linux Ubuntu 6.06 no wireless device was detected. I then installed linux-wlan-ng. After rebooting, a wireless device was detected, although I still do not have an internet connection. Can someone please help me through this?

---

### Post by Sketch on 2006-08-30
this is a Reference

[http://ubuntuforums.org/showthread.php?t=246600](http://ubuntuforums.org/showthread.php?t=246600)

to the original convo posted in the beginner forums

---

### Post by Sketch on 2006-08-30
----Still Can Not Connect To Internet------

Can Someone Please Help Me

---

### Post by Sketch on 2006-08-31
Another Day Without Internet...Anyone??Help??Please

---

### Post by tormod on 2006-09-20
If it's a USB device, please use "lsusb" to identify the device. Then report back here.

If you're gonna use linux-wlan-ng, [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) might help, the configuration instructions are valid for all prism2 (also not usb) devices I guess.

---

