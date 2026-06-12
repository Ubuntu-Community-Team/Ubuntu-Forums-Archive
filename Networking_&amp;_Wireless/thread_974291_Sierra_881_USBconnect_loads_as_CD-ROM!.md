---
title: "Sierra 881 USBconnect loads as CD-ROM!?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by natarnsco on 2008-11-07
I just received my new Sierra 881 USBconnect card this morning and after reading a bunch of threads the last few days about configuring it to access AT&T's 3G networks I was confident it would work.

However, when I plug it in, it mounts as a CD-ROM drive.  I have searched and can't find where anyone else had this problem.

When I right click on the cd icon and select Properties and then Volume it says:
"Mount Point:  /media/TRU-Install"
"File System:  iso9660"
"Mount Options: ro nosuid nodev"

I tried changing the Mount Point to /dev/ttyUSB0 and unplugging the device and plugging it back in but then it says it can't mount the device.

How can I make it get recognized properly?

Gutsy 7.10
kernel 2.6.22-15-generic
'modinfo sierra' says the driver is installed
It shows up on lsusb


eta: Okay, I just read that for kernel 2.6.22 you have to install a patch and re-compile the kernel for TRU-Install devices.  I've been trying to avoid upgrading to 8.04 since everything works right now on my laptop but I guess I don't have a choice if I want this aircard to work, because I don't want to have to keep up with a custom kernel.

---

