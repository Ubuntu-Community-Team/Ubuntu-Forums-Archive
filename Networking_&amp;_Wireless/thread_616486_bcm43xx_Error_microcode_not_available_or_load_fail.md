---
title: "bcm43xx Error: microcode not available or load failed"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by markdjones82 on 2007-11-18
All, a while back I had installed the restricted drivers, but my computer would freeze as soon as I opened firefox.  So I unisntalled.  Well I was checking some of my /var logs because my computer is not coming up sometimes after a long period of time but I noticed the error is coming up over and over in like the kern.log.

Any ideas on what to look at?

---

### Post by Blutack on 2007-11-18
It is hunting for the firmware for the wireless card.  This firmware is not included with ubuntu because of legal reasons, although for some reason they included the driver.
Personally, I used ndiswrapper with my bcm43 because the included driver is a bit sketchy.  You might want to look here
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by rosegarden78 on 2008-01-21
I thought bcm43xx was in the repos.  There's also an fw-cutter.  Anyway all you do is install bcm43xx or fw-cutter package.  Then from a terminal type

sudo modprobe bcm43xx
nm-applet

---

