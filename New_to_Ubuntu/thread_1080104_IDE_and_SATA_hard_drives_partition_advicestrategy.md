---
title: "IDE and SATA hard drives partition advice/strategy"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-25
hello,

i'm planning to set up a dual boot with XP and ubuntu.

right now, i have XP in a single partition on my 40GB IDE hard drive.

i have a 1TB SATA hard drive that im ready to install if i can get a clear strategy on how to set up the partitions.

from what i've read, having IDE and SATA drives may be inviting some problems, but since my Dell dimension 4600 (has one PATA and two SATA available on mobo)doesn't appear capable of having two PATA drives, i had to get a SATA as my second drive.  

i would prefer to use the blank SATA drive as my linux drive and install ubuntu on there, not touching or shrinking the XP IDE drive and possibly screwing up my XP which i need and would really not like to reinstall.

however, it seems that some people have been having problems with the MBR, etc when putting linux on a separate drive.

would people recommend putting ubuntu on the IDE drive with the XP and having the ubuntu/home on the secondary SATA drive?

or should i be putting everything ubuntu on the SATA drive and leave the IDE alone?

and where does the GRUB go? on the linux SATA drive or the XP IDE drive?

ive been trying to understand this thread [http://ubuntuforums.org/showthread.php?t=1070698&highlight=home+partition](http://ubuntuforums.org/showthread.php?t=1070698&highlight=home+partition) since it seems like that's what i want to do, but being a complete noob, it's rather confusing to me.

was the solution installing just the GRUB onto the XP drive?  or was the GRUB on the second drive and boot sequence was changed in BIOS to go with the GRUB on the second linux drive?

thank you for the help,

---

### Post by cjv8888 on 2009-02-25
> **nachos99 said:**
> hello,

i'm planning to set up a dual boot with XP and ubuntu.

right now, i have XP in a single partition on my 40GB IDE hard drive.

i have a 1TB SATA hard drive that im ready to install if i can get a clear strategy on how to set up the partitions.

from what i've read, having IDE and SATA drives may be inviting some problems, but since my Dell dimension 4600 (has one PATA and two SATA available on mobo)doesn't appear capable of having two PATA drives, i had to get a SATA as my second drive.  

i would prefer to use the blank SATA drive as my linux drive and install ubuntu on there, not touching or shrinking the XP IDE drive and possibly screwing up my XP which i need and would really not like to reinstall.

however, it seems that some people have been having problems with the MBR, etc when putting linux on a separate drive.

would people recommend putting ubuntu on the IDE drive with the XP and having the ubuntu/home on the secondary SATA drive?

or should i be putting everything ubuntu on the SATA drive and leave the IDE alone?

and where does the GRUB go? on the linux SATA drive or the XP IDE drive?

ive been trying to understand this thread [http://ubuntuforums.org/showthread.php?t=1070698&highlight=home+partition](http://ubuntuforums.org/showthread.php?t=1070698&highlight=home+partition) since it seems like that's what i want to do, but being a complete noob, it's rather confusing to me.

was the solution installing just the GRUB onto the XP drive?  or was the GRUB on the second drive and boot sequence was changed in BIOS to go with the GRUB on the second linux drive?

thank you for the help,

If your BIOS is capable of selecting which drive to boot first, the preferable choice would be to install Ubuntu into the SATA drive and also select to have grub installed on this drive so you are leaving the IDE drive entirely untouched.
When you install, select the manual partitioning to pick the SATA drive.  Then when you get to the part when there is an Advance button to press, you can select to have Grub put onto this drive.  Grub should automatically detect the XP and chainload it onto the Grub menu.

---

### Post by handy on 2009-02-25
Hopefully you may find some use in this how-to:

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*

---

