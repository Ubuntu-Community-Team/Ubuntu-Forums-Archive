---
title: "Broadcom Wireless"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by schmickey on 2010-09-07
Okay, I followed the instructions at the link below:
[Install driver from USB drive]("http://forum.notebookreview.com/6642885-post1573.html")

If I boot from my Lucid LiveCD on the flash drive I can install the Broadcom wi-fi driver and can use it.  But after installing to the hard drive I am not able to install the driver.  The ethernet doesn't work either so I'm trying to install it from the USB flash drive.

Step #5 at the link doesn't tell me exactly WHAT to put into sources.list.  The broadcom .deb will begin to install and then chokes because it can't find the dependencies on the flash drive... even though it is symlinked to a "cdrom" directory in the root of the hard drive.

Any ideas?  The OP of those instructions has not replied.

---

### Post by coffeecat on 2010-09-07
Hi

You're better of with Ubuntu documentation. :) See:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It includes how to set up the CD as a repository (you don't need to edit sources.list directly) and some other useful information.

---

### Post by schmickey on 2010-09-07
> **coffeecat said:**
> Hi

You're better of with Ubuntu documentation. :) See:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It includes how to set up the CD as a repository (you don't need to edit sources.list directly) and some other useful information.

I got it working... I honestly don't know how -- I was trying several angles of attack at once.  But it's working now.  Thanks for the reply.  Now if I can only get the Atheros AR8151 ethernet working....

---

