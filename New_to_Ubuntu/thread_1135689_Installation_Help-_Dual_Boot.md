---
title: "Installation Help- Dual Boot"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by CoffeyLover on 2009-04-24
Ok guys, help me out on this one. I am going to partition my hard drive (Currently running XP) and install ubuntu. I've done it before, and it is fairly easy. However, I have a problem. Other people occasionally use my computer. But when they turn it on, and it comes up with the boot loader, they flip out. Is there any way to make it so XP boots automatically except when a key on the keyboard is held down or something? (I know this is the way mac does it) Basically I want it to seem like ubuntu is not there (So others will not be confused). Thanks!

---

### Post by mikewhatever on 2009-04-24
The easiest way to do it is to install startupmanager from the repositories. Once you have it, reduce the timeout to 3 seconds and set Windows booting by default.

---

### Post by Melk79 on 2009-04-24
The longer method would be to edit your menu.lst file under /boot/grub using the terminal/ text editor.

Enter this in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

That will bring up the text editor and you will need to change the default boot line to correspond with XP and you could change the delay time to 2 or 3 seconds (to give you enough time to boot ubuntu when you use it).

If you read through menu.lst it explains the different choices, but it is important to remember the numbers start with 0 and "Other Operating Systems" is also a number.  So let's say your boot screen shows
Ubuntu 8.10, kernel 2.6.27
Ubuntu 8.10 (recovery mode)
Debian memtest+
Other Operating Systems:
Windows XP

You would need to change the default boot line from 0 to 4 in order to boot XP by default.  If you ever add another kernel line, you may need to change it to 6 otherwise you'll keep booting into the memtest.

Startup Manager is much easier

---

### Post by lkraemer on 2009-04-24
Lover,
If they are so confused with the Grub menu, I personally wouldn't want
them mucking around in my computer..............Good Luck.

To partition your Hard Drive download the LiveCD of gparted.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Yes, it re-sizes your Vista Partition too!

Then to recover Windows so that it will boot after the Master Boot
Record (MBR) gets messed up download the LiveCD of Supergrub.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Also get the LiveCD's of:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Here is the BEST Dual Boot site available.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I'll toss in Clonezilla, because You will need it at some point.
[http://clonezilla.org/](http://clonezilla.org/)

The best of all is VirtualBox, which lets your Linux Host run
Guest OS's (XP) and other Distros.
[http://www.virtualbox.org/](http://www.virtualbox.org/)
Maybe you just want to install VirtualBox, and then Install XP as a
Guest OS inside VirtualBox.  Better than Dual Boot in my book!

And finally there is distrowatch.  See what all those Distro's are up to.
[http://distrowatch.com](http://distrowatch.com)

lkraemer

---

