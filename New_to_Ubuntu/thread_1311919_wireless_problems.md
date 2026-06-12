---
title: "wireless problems"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by cack- on 2009-11-02
so i installed ubuntu 9.10 on my laptop, fresh install, first time using ubuntu.  when i installed it everything seemed to work well, but my wireless doesnt work. at first it didnt pick up the wireless at all. now after some playing around with different methods i've found online i got it to atleast show the "wireless networks" under where it shows my wired connection

problem is, it doesnt show any of my wireless networks. when i go to system>admin> hardware drivers. it shows a wireless card driver but it says "this driver is not activated"

my computer is a hp pavilion dv9700

---

### Post by clhsharky on 2009-11-02
HI

Hope this helps
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

and this
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by anewguy on 2009-11-02
For that non-activated driver, click it and activate it and see what happens from there.  Ubuntu obviously thinks you need the driver because it has identified some piece of hardware it thinks needs it.

Let us know how it goes.

This is 1 of 2 things I have noticed so far for wireless after the upgrade:

- you may need to reinstall your wireless driver or re-activate the restricted driver

- if an atheros chipset, you will need to edit the /etc/modprobe.d/blacklist-ath_pci.conf file and change the last line to have a "#" character in front of it to comment it out, then reboot.

Dave :)

---

