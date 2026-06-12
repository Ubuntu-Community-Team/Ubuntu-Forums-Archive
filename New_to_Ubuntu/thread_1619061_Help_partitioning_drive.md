---
title: "Help partitioning drive?"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by momrocker on 2010-11-11
Hey guys, I have been installing Ubuntu with Wubi for the past year or two I've been using Ubuntu, and since my computer has been having some trouble in 10.04 and 10.10 (like **+10 minute boot times** (which I haven't experienced until 10.04 came out)), I want to partition my drive and install one of the older versions on my computer, like 8.04. Since this is my first time  partitioning a drive, I have a few questions:

Will partitioning a drive cause data loss, like formatting a drive?

Since I have Windows 7 installed, will shrinking the windows partition in Ubuntu with gparted hurt/break the data on there? [This]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") article talks about creating a recovery disk and a whole bunch of stuff that I wouldnt mind doing, although I would like to know in advance if it is mandatory.

And, are there any articles/pages I can read on partitioning since I'm new to the concept?

Thanks in advance!

EDIT: I forgot to post my system specs, whoops :P
[Here]("http://www.amazon.com/Toshiba-NB205-N210-NB200-10-1-Inch-Netbook/dp/B002BDUAEK") is my laptop on amazon with all the same specs. Since it is a netbook I will need to boot any live cds with a usb disk drive, will that cause problems?

---

### Post by NightwishFan on 2010-11-11
You might find this link helpful:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

> Will partitioning a drive cause data loss, like formatting a drive?

No, as you can have up to four normal partitions on a drive, and more if you use something a bit more complicated called logical partitions. You have to have free disk space to make a partition, which involves shrinking other partitions to make the room. Here is how to shrink a partition in Windows 7:
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)


> Since I have Windows 7 installed, will shrinking the windows partition in Ubuntu with gparted hurt/break the data on there? 

That is a possibility. Windows in general does not like to be moved around except by it's own tools, and might throw a fit. See the above for how to do so.


> And, are there any articles/pages I can read on partitioning since I'm new to the concept?

Generally once you shrink the partition of Windows it is easy to use the Ubuntu installer to fit Ubuntu in there nicely. Here are some links:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://en.wikipedia.org/wiki/Disk_partition](http://en.wikipedia.org/wiki/Disk_partition)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)


> Thanks in advance!

Sure no problem! :)


 > Since it is a netbook I will need to boot any live cds with a usb disk drive, will that cause problems?

No it is fine. You can use this program to create an Ubuntu live CD, which you can then install from.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


Some post notes for you. Hardy reaches end of life for desktop edition in April of 2011, so you might want to start a new thread about the boot issues (Which might have been wubi releated) and move to 10.04 before April of next year.


Here are some links related to your hardware:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Toshiba%20NB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Toshiba%20NB205)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

---

### Post by momrocker on 2010-11-11
Wow thanks! Yeah I tried opening a thread on the boot issue a while back but nobody responded. Maybe I should try again. Thanks for all the articles especially! Ill have to read them once I get some time...

---

### Post by NightwishFan on 2010-11-11
Sure, no problem. Hopefully we can get it working. :) I also just added some links about the Toshiba netbook.

---

### Post by NightwishFan on 2010-11-11
Found a fix to the slow boot time:
> Bootup time

The boot time is with the default settings horrendously slow. A simple change in the BIOS will speed up the boot time to less than 30 seconds.

    * Press F2 on machine boot to enter the BIOS
    * Select the 'Advanced' tab
    * Change SATA controller mode from AHCI to Compatibility 

You might get to use 10.04 after all. :) This page (also linked above) has a few more fixes. [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

---

