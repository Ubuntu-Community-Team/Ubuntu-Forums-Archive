---
title: "atmelwlandriver"
date: 2005-03-25
forum: Networking &amp; Wireless
---

### Post by zardoz on 2005-03-25
I just gave the atmelwlandriver ([http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html)) a try (after I got stuck with ndiswrapper), to get my Siemens USB Wlan Adapter 11Mbit to work.
Now ... new problems :-(

When I do "sudo make usb" following error messages show up:

...../reset_device.c:24:17: hub.h: File not found
...../reset_device.c:25:17: hcd.h: File not found

So I just searched them on my system to link them directly, but hub.h isn't anywhere (hcd.h was there). I got the kernel-headers installed.
Any idea?

---

