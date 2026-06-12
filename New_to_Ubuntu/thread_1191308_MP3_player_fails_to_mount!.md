---
title: "MP3 player fails to mount!"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Java Geek on 2009-06-18
Hello, I have a Samsung YP-Z5 4GB MP3 player. I plugged it into the computer (via usb) and I am getting no result that kubuntu even knows that it is there. I'm going on a trip tonight and any quick advice would be very helpful.

---

### Post by Sealbhach on 2009-06-18
Please type lsusb in a terminal and copy and paste the output from that here.


.

---

### Post by Java Geek on 2009-06-18
ok here's the output
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 06a3:0471 Saitek PLC Cyborg Graphite Stick
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Sealbhach on 2009-06-18
Can you look at the settings in your camera?  Change the USB setting to "Mass Storage device" (UMS) rather than MTP.

.

---

### Post by Java Geek on 2009-06-18
> **Sealbhach said:**
> Can you look at the settings in your camera?  Change the USB setting to "Mass Storage device" (UMS) rather than MTP.

.

It's an MP3 Player... Besides I dont know if you can do that on this model

---

### Post by Sealbhach on 2009-06-19
OK sorry, about that. Been Googling and this thread seems to have the most info:

[http://www.linuxquestions.org/questions/linux-hardware-18/using-a-samsung-mp3-player-in-linux-501631/](http://www.linuxquestions.org/questions/linux-hardware-18/using-a-samsung-mp3-player-in-linux-501631/)

First thing to check is that you have the latest firmware from Samsung, that seems to solve most problems. If that doesn't work, try installing the libmtp packages.


.

---

### Post by sampath1 on 2009-06-19
Hi,

carefully look for your camera settings.

thanks

---

### Post by Sealbhach on 2009-06-19
Lol! It's an MP3 player.:D

.

---

### Post by dyingsun on 2009-06-19
Don't know if it's relevant in this case, but I manually unmount any USB storage devices, including my mp3 player, before I disconnect it physically, otherwise any software is looking for the old connection. Does it still show up in your Places, even if it is inactive? When that happens to me, I either sudo umount it or you could just reboot. I know mine's probably not configured properly, I'll be overhauling soon as semester's over!

---

### Post by Chronon on 2009-06-19
If it's an MSC device then you should always unmount before disconnecting.  If you don't you're asking for file system corruption.

By the way, [this page](http://www.ubuntuhcl.org/browse/product+samsung-yp-z5?id=649) says it has MSC mode, though not how to switch to it.  Do you not have any documentation anymore?  (I know I tend to promptly lose mine with most devices.)

---

