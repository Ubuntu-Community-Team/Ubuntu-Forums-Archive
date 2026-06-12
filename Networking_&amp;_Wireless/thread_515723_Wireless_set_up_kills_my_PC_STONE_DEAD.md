---
title: "Wireless set up kills my PC STONE DEAD"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by yakobb on 2007-08-02
I eventually almost got my wireless card working, after installing Ndiswrapper and the appropriate driver. But then I restarted the PC, and It hung at the Grub "loading stage 1.5" stage. I then had to reinstall ubuntu and use the super GRUB disk. Installed Ndiswrapper again, again the same problem.. this time boot sector of my 1st hard drive - with windows and all of my important stuff - became corrupted! Was starting to panic, but windows setup disk saved the situation.

Now, it seems a bit unreasonable to me that just installing a wireless driver should screw up my PC so badly.. essentially turning it into a big expensive door stop. any suggestions? To install the driver I followed these two steps:

[http://ubuntuforums.org/showpost.php?p=2998944&postcount=3](http://ubuntuforums.org/showpost.php?p=2998944&postcount=3)

[http://ubuntuforums.org/showpost.php?p=3109604&postcount=18](http://ubuntuforums.org/showpost.php?p=3109604&postcount=18)

---

### Post by ddrichardson on 2007-08-02
I can't see how following these guides could cause this problem, especially as the drives have corrupted at different positions in the two times it has happened. Network card shouldn't have any way to interfere with the drives or controller.

Is Windows running flawlessly, or have you noticed any other problems - high fragmentation, frequent scandisk requests or slow down in Windows?

---

### Post by yakobb on 2007-08-03
No, no problems with windows at all.. I think it might have been something to do with GRUB as the first time the drive was ok, but was still hanging on startup. But I don't see why wireless drivers would interfere with grub?

---

### Post by ddrichardson on 2007-08-03
Possibly, but check the disks with scandisk first - just to make sure the drives are OK.

---

