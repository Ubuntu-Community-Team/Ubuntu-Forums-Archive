---
title: "BCM4306, tried how to's but still not working"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2006-11-11
Hi, I tried out this how to: [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

I have not had any luck though with my Asus wifi card, it has a Broadcom chip, the BCM4306.

Network manager does not show an option to enable wireless, only an option to enable network (and thats ueseless because my only access to the net right now would be through wireless).

Has anyone managed to get this to work?

Is there a how to on how to use ndiswrapper with bcm4306?

---

### Post by PartisanEntity on 2006-11-11
Here some screenshots, perhaps they will help:

[IMG]http://i15.tinypic.com/47lo3n6.jpg[/IMG]

[IMG]http://i15.tinypic.com/40c6g7b.jpg[/IMG]

[IMG]http://i15.tinypic.com/2ljl278.jpg[/IMG]

[IMG]http://i15.tinypic.com/48xtmjl.jpg[/IMG]

[IMG]http://i7.tinypic.com/42su4i1.jpg[/IMG]

[IMG]http://i15.tinypic.com/2cy4kmp.jpg[/IMG]

[IMG]http://i15.tinypic.com/2eyxiqv.jpg[/IMG]

---

### Post by kybishop on 2006-11-12
[http://apt.ubuntu.org.tw/ubtw/bcm43xx-firmware/](http://apt.ubuntu.org.tw/ubtw/bcm43xx-firmware/)

after seeing it once, loseing the link, then looking everywhere, i finally found it.

its a deb that installs the native drivers for the bcm4306 hardware.


all you have to do is burn it to a cd, flash drive, etc. and then put it on the computer, then run the deb, and bam, wireless works (after a little iwconfig) :D

---

### Post by PartisanEntity on 2006-11-13
Thanks very much!

I am going to give it a try. But some questions first:

1. Do I need to disable any other drivers before installing the one you linked to?
2. I guess this deb is compatible with Ubuntu 6.06?

---

