---
title: "iPod Touch 4 not mounting in Ubuntu 10.04"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by John.b.Goode on 2010-10-21
Hello folks,
Here's the scoop: when I plug my iPod Touch 4 into my computer (ubuntu 10.04), nothing visibly happens. The iPod beeps a couple of times, but the device doesn't come up on the desktop, and it doesn't show up in rhythmbox. I'm pretty sure that I'm the one that bunged things up--I tried, unsuccessfully, to install the software necessary to initialize my iPod on Ubuntu. So I've messed something up. Short of reinstalling the O/S, is there something I can do to get things working? 
Thanks in advance for your help.

---

### Post by P4man on 2010-10-21
Yeah, you could send an email to Steve Jobs and ask if he wants to disclose the protocols needed to interface with his toys, or release itunes for linux.

Since that isnt likely to help, you can give this a shot:
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by John.b.Goode on 2010-10-25
Thanks for your reply P4man, but I have been to that website already, and have added the ppa at [https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa") to my sources list and ran the update, to no avail.

---

### Post by P4man on 2010-10-25
You dont have to only update, you also have to actually install those apps. Now that you added them to your software sources, find them in software center: libimobiledevice, possibly ifuse etc. Not sure which ones depend on what, just see the list on their website.

---

