---
title: "USB Wireless Stick and USB Errors"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by llamabr on 2008-01-07
Hello, Ubuntu-ers,  I'm hoping someone can help me decode some errors I'm getting, and make my ZyXel g-220 v2 work again.  As noted here:

[http://www.murrayc.com/blog/permalink/2007/09/07/linux-compatible-wireless-usb-adaptor-slightly-better-in-ubuntu-gutsy/](http://www.murrayc.com/blog/permalink/2007/09/07/linux-compatible-wireless-usb-adaptor-slightly-better-in-ubuntu-gutsy/)

It worked flawlessly the first time I plugged it in.  However, when I woke up yesterday, it was no longer listed in network-admin (a gnome utility), not did ifconfig list it as eth1, as it did previously.  Additionally, I'm seeing this error in dmesg, and on bootup:

brock@vader:~$ dmesg | grep error 
[   16.433292] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not 
found.
[    4.408000] usb 1-1: device not accepting address 2, error -71
[   19.944000] usb 5-1: device descriptor read/64, error -110
[   35.160000] usb 5-1: device descriptor read/64, error -110
[   50.488000] usb 5-1: device descriptor read/64, error -110
[   65.704000] usb 5-1: device descriptor read/64, error -110
[   76.328000] usb 5-1: device not accepting address 4, error -110
[   86.848000] usb 5-1: device not accepting address 5, error -110
[  102.200000] usb 5-5: device descriptor read/64, error -110
[  117.416000] usb 5-5: device descriptor read/64, error -110
[  132.744000] usb 5-5: device descriptor read/64, error -110
[  147.960000] usb 5-5: device descriptor read/64, error -110
[  158.584000] usb 5-5: device not accepting address 8, error -110
[  169.104000] usb 5-5: device not accepting address 9, error -110
brock@vader:~$ 

When I plug in the usb wireless stick, it'll give this error over and over, trying different addresses.  Is this error a hardware problem?

The stick works fine when plugged into a MS-XP laptop, and my USB Optical mouse functions perfectly.

I know you won't believe it, because I never believe when others say it, but I didn't touch anything between when it worked, and now that it doesn't.  I did a complete re-install this morning, and it's still giving the same errors.

Thanks for any help you may throw my way.  I don't really know where to start.

Robert

---

### Post by llamabr on 2008-01-08
Actually, I solved this one myself.  I ran a 

rmmod ehci-hcd

which removed the module which, I believe, is responsible for high speed 2.0 USB devices.  Now my stick is running on the slow 1.1 speed, which is plenty fast enough.

Probably I'll have to blacklist this module to keep it from loading on reboot, but I havn't rebooted yet to find out.

Read more about ehci-hcd here:

[http://www.linux-usb.org/FAQ.html](http://www.linux-usb.org/FAQ.html)

Robert

---

### Post by Hightide on 2008-01-08
well done  :)

---

