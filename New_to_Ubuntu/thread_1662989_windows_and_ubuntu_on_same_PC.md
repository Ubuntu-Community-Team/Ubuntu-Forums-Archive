---
title: "windows and ubuntu on same PC"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by smooth65 on 2011-01-09
Hi everyone. Newbie here. I just insalled ubuntu with the intentions of keeping windows 7 also. When I boot my laptop, it does not give me the option of which OS i can run. I simply boots up Unbuntu each and everytime. I remember checking the option to run ubuntu on same PC as windows. Did I do something wrong? It appears that I only have ubuntu and I may have accidently erased windows? Any ideas?

---

### Post by abdulapopoola on 2011-01-09
Could you be more explicit? It is possible that you've accidentally erased your Windows 7; alternatively it might be that GRUB doesn't see the Windows bootloader and you might have to configure that.

[http://abdulapopoola.wordpress.com](http://abdulapopoola.wordpress.com)

---

### Post by wilee-nilee on 2011-01-09
In the Ubuntu terminal run this command and post the output.
sudo fdisk -lu

---

### Post by smooth65 on 2011-01-09
ok what am i looking for exactly in the link you provided. Not sure how to describe in more detail. Very very new to all of this but excited to learn.

---

### Post by smooth65 on 2011-01-09
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001dbe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   299808767   149903360   83  Linux
/dev/sda2       299810814   312580095     6384641    5  Extended
/dev/sda5       299810816   312580095     6384640   82  Linux swap / Solaris
smooth65@smooth65-Satellite-L355:~$


This is what I got in terminal. Not sure what all this means

---

### Post by wilee-nilee on 2011-01-09
It is the lists of the partitions that contain the operating system. I see no windows there, it shows a 160 gig hd, if that's all there is then you installed Ubuntu in place of windows.

Do you have a reinstall dvd for windows?

---

### Post by smooth65 on 2011-01-09
Yes, thank goodness I have a windows 7 DVD

---

### Post by wilee-nilee on 2011-01-09
> **smooth65 said:**
> Yes, thank goodness I have a windows 7 DVD

So it sounds like nothing is actually on there now that means anything, other then the Ubuntu install. You could shrink the Ubuntu but a new install of both with windows first would be prudent. Before you reinstall Ubuntu though, shrink W7 with its disk manager leaving a unallocated space. You will have to the boot the live Ubuntu to install, but you will want to build the partitions first in Ubuntu with gparted, and use the custom install. I will or another will help you where needed.

---

### Post by abdulapopoola on 2011-01-09
Hey smooth65, good luck...
Too bad you had to wipe your computer first. Have fun with Ubuntu, it sure is great.
You can google freecirclemagazine for titbits.

Have fun.
[http://abdulapopoola.wordpress.com](http://abdulapopoola.wordpress.com)

---

### Post by smooth65 on 2011-01-09
How do I shrink windows 7 if I dont have it anymore. Do I have access still to windows disk manager?

---

### Post by Kasami on 2011-01-09
> **smooth65 said:**
> How do I shrink windows 7 if I dont have it anymore. Do I have access still to windows disk manager?

Windows is gone forever. You need to reinstall Windows 7 off of your installation DVD and then shrink the partition size with disk manager.

---

### Post by Quackers on 2011-01-09
wilee-nilee means after you have re-installed Win 7.
I'm wondering if you installed Ubuntu 10.10 and chose the "install alongside" option?

---

### Post by smooth65 on 2011-01-09
Yes I did install version 10.10 and I did choose the along side option. Thanks for your help thus far guys. It really means alot to me

---

### Post by Quackers on 2011-01-09
The 10.10 installer is known to eat existing operating systems when the "install alongside" option is used, sadly. Bugs have been recorded regarding this serious issue.
It is recommended that you use the "specify manually" option and create your own partitions for Ubuntu that way.

---

### Post by smooth65 on 2011-01-09
Ok thanks yall. I will give this a try and report back to ya. Thanks again.

---

### Post by Phillip Spencer on 2011-01-09
Hi,

Sorry to read about your problems. You will get some good advice on this forum. Lots of us have stumbled early on with installing Ubuntu alongside Windows. Shame you have been caught by an apparent bug in 10.10.  I hope you had backed up your user data on Windows before the install.  Always strongly recommended prior to any install or touching the partitions.

It has been suggested that you manually manage the partitions. There are very powerful tools for managing the partitions, such as gparted.  My two-cents worth (as someone who learnt the hard way) is that if you are new to this, read up first, then read again before doing anything.  Then take it step by step and if you hit a problem: STOP immediately. Check this forum and if you can't find the issue post for help.  There are some old hands at this, such as Wilee-Nilee who has already posted to this thread (plus, for me, oldfred and RanchHand) who have really helped out. For me, they took me through step by step to recover over a week (took a long time because I didn't stop and compounded the problem!)

Good luck,
Phillip

---

