---
title: "Full version upgrade"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-06-09
Ok, i got a fresh install of windows xp loaded... i dont have a cd rom drive nor do i have a floppy drive.. i had a wubi version of ubuntu and want to upgrade to the full version... How can i do this...

---

### Post by keplerspeed on 2009-06-09
Maybe by USB??? [http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Boot from live usb (if you computer can boot from usb) and install ubuntu.

---

### Post by Steelmourne on 2009-06-09
From the wubi install, assuming its Ubuntu 9.04/ Jaunty Jackalope, obtain a 2GB USB drive, stick it in a free port, then go to system administration usb startup disk (it may be in preferences, I forget which), select the usb in the option that you plugged in along with a copy of the ubuntu iso and hit create. Then reboot the pc into xp (shudder) go to add/remove applications, remove wubi.

Finally reboot the pc with the usb in the drive. You may have to go to BIOS and change the boot order. Install from the USB and repartition the hard drive when asked.

---

### Post by Cheesemill on 2009-06-09
You can't upgrade from Wubi to a full install, however using the steps above you can do a clean full install and then just remove Wubi afterwards from Windows 'Add or Remove Programs'.

Cheesemill

---

### Post by philinux on 2009-06-09
Yes you can.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
Scroll down to this section..

> Can I move my virtual disk file to a dedicated partition?

You can use LVPM to transfer your installation. A guide and support forum for LVPM is available here.


[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by Cheesemill on 2009-06-09
I stand corrected :)

---

