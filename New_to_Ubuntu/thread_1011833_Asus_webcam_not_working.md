---
title: "Asus webcam not working"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by The Judderman on 2008-12-15
Asus webcam
Dear all,

I have an Asus Laptop, with integrated webcam that doesn't seem to work in 8.10. THis is the output of the lsusb command:

Bus 003 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So I presume that I need the Syntek driver. How do I install that? SKype, Ekiga and aMSN all say that no webcam is connected!

I hope that you can help me.

The Judderman

---

### Post by NewJack on 2008-12-15
What version of Ubuntu are you running?

---

### Post by The Judderman on 2008-12-16
Intrepid 8.10

---

### Post by Kobalt on 2008-12-16
Check out this post about a Syntek webcam and Ubuntu 8.10 : [http://ubuntuforums.org/showthread.php?t=966357](http://ubuntuforums.org/showthread.php?t=966357)

---

### Post by The Judderman on 2008-12-17
Thanks for that. I looked at the post and followed this "How to" [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek) (Thankfully my French is good), but still with no success.

dmseg | tail (not sure what this does, but this was one of the checking things) posts this:

dmesg | tail
[   50.184258]   groups: 1 0
[   50.184267]   domain 1: span 0-1 level CPU
[   50.184271]    groups: 0-1
[  146.860211] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  147.860240] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  148.860149] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  171.600446] NET: Registered protocol family 10
[  171.601612] lo: Disabled Privacy Extensions
[  171.602882] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  182.064017] ath0: no IPv6 routers present

---

