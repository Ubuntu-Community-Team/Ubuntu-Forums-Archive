---
title: "Booting From USB - Want to Prevent HDD From Mounting"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by pycal on 2009-07-11
I'm really sorry if this has already been posted about - I did a search but couldn't find information on this specific subject (only problems with USB drives mounting!)

I am currently booting an ubuntu 9.04 64-bit persistent live session from a 2.0gb USB drive.  Everything boots fine, and so far I have been able to do things like install drivers for my wireless card and install applications from the package manager.

Currently when I boot, my laptop's internal hdd is mounting and continues to spin.  I am wondering if there is a way for me to prevent it from mounting/spinning.  I think this will probably save some power consumption and boost my battery life a bit.

Thanks in advance.

---

### Post by LewRockwell on 2009-07-11
you didn't provide specific information for the laptop you have so I'll just toss the ball around a bit...

SOME hard drives in SOME laptops are very easy to remove

if yours is one of those then that is what I would do(perhaps creating some sort of cover or plug for the area where the drive is located so that cooling air flow is not disrupted or significantly rerouted)

just a thought...

.

---

### Post by pycal on 2009-07-11
I have an hp dv6000, and yes the hard drive is very easy to remove.  This is definitely not the solution I'm looking for though - I would like to be able to just plug my usb key in, boot ubuntu, but not have my hard drive spinning/generating heat/wasting battery power.

---

### Post by LewRockwell on 2009-07-11
[http://bbs.archlinux.org/viewtopic.php?pid=565427](http://bbs.archlinux.org/viewtopic.php?pid=565427)

I'm thinking hdparm is installed by default but if it isn't then I'm sure it's in the repositories

[http://en.wikipedia.org/wiki/Hdparm](http://en.wikipedia.org/wiki/Hdparm)

.

---

