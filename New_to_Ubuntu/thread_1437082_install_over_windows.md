---
title: "install over windows"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by rigidigital on 2010-03-23
When i try to install it says i will lose XP ??

---

### Post by andrewthomas on 2010-03-23
It should give you the option to install side-by-side and choose between at boot.  Are you using the desktop live cd?

---

### Post by QIII on 2010-03-23
Defrag the drive with XP at least twice.

Use the utilities in XP to modify your partitions and gain some space to install Ubuntu to.  Windows will figure out how all those files are arranged and change the partitions appropriately.  

I believe that there is an option to install Ubuntu to the largest contiguous area of free space.  (It's been a long time since I set up a dual boot on a single drive, so I am a bit rusty here.)

If you are not familiar with installing Linux, I would not recommend attempting to manually configure your partitions at this point.  You could make a horrible mess.

---

### Post by AlanR8 on 2010-03-23
Just back up EVERYTHING before you start messing around with dual boots then it doesn't matter if it all goes pear shaped!

As stated in the reply above, you will get an option in the set-up to dual boot. In my experience, if you want to dual boot, you MUST install Ubuntu AFTER XP. 

Something to do with the master boot record on the hard disk.

Done it this way half a dozen times and no issues, but NEVER without a full data backup of the files on Doze AND knowing where the original Doze installation disks are!

Lots of people forget that last bit........

---

### Post by Calash on 2010-03-23
Be careful with this as it can be very easy to do it wrong and overwrite your XP.

I assume you are looking to Dual boot both XP and Ubuntu?  Make sure to read all the screens and do some research here on how to configure your computer to Dual Boot.  There are many great guides to follow.


A few things


1 - Make sure to read before pressing buttons (Yes, I have said this alot, but people tend to skip over and cause themselves problems)

2 - Backup your important information before beginning, just in case.

3 - If in the future you decide to get rid of Ubuntu it is not as simple as removing the partition.  Should this time come make sure to come back here and do research as you will have to change back to a Windows MBR to run XP alone again.


Good luck.

---

### Post by anoop999 on 2010-03-23
I found it better to use GParted on the Ubuntu live CD to shrink the windows XP partition and partition the drive how I wanted it, before installing Ubuntu.

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

(Note: you must not shrink Vista or Win7 partitions using GParted)

---

