---
title: "Issues with usbip [armhf Xenial]"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by schmidtbag on 2016-12-19
I have an old Beagleboard-xM (an ARMv7 platform) that I wanted to try using as a wireless USB hub.  To do this, I was planning on using the program "usbip".

I've heard that the usbip package should be avoided (it doesn't work anyway), and install linux-tools-generic instead; that contains the program and is more up-to-date.  The tricky part is how this package is kernel-specific and I have a finite amount of kernels available to me for this platform.  Currently, I managed to get a linux-image-4.9.0 (from Beagleboard's repos) and a linux-tools-generic-4.9.0.x.x from Zesty.

So far this appears to be working ok on the Beagleboard, but not on the remote system.  When using the "usbip attach" command, it says:
```
usbip: error: recv op_common
usbip: error: query
```

This occurs on both an x86-64 Arch install, and a separate x86-64 Debian install.

---

