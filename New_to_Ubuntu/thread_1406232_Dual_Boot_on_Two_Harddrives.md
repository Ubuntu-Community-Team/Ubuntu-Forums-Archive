---
title: "Dual Boot on Two Harddrives"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by ajdrew06 on 2010-02-13
Hi All,

I have Ubuntu 9.04 and Windows 2000 on two separate hard drives in my desktop.  Ubuntu is on (hd0,0), and I believe Windows is on (hd1,0).  I added the following lines to /boot/grub/menu.lst

title         Windows 2000
rootnoverify  (hd1,0)
chainloader   +1
makeactive

In my BIOS, I have my Ubuntu hard drive set to boot first.
When I select Windows 2000 on the grub boot menu, it says

Starting up...

But it doesn't load.  There are no error messages.  It just lags.  How might I fix this problem?

If I change my BIOS so that my Windows 2000 hard drive boots first, Windows loads fine.

Help is appreciated!  Thank you!

---

### Post by nhasian on 2010-02-13
leave your bios set to boot windows first.  if you change it, windows wont work.  now you will need to install grub onto the windows hard disk so you can have a boot menu to choose which OS to load:

[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

---

### Post by oldfred on 2010-02-13
You should be able to get this to work with grub. I prefer that each drive have its operating systems boot loader. If ever any issues you can still change BIOS and boot the other drive.

The makeactive would have to be before the chainload command as chainload is what switches to windows. The makeactive should not be required if you have the boot flag set on the windows partition. It is more for those who have more than one copy of windows. You also probably need map commands to make windows think it is the first drive.

title        Microsoft Windows 
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

To see your entire configuration and confirm we have the correct partitions:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by ajdrew06 on 2010-02-13
> **nhasian said:**
> leave your bios set to boot windows first.  if you change it, windows wont work.  now you will need to install grub onto the windows hard disk so you can have a boot menu to choose which OS to load:

[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

THIS WORKED!! Thank you so much!

---

