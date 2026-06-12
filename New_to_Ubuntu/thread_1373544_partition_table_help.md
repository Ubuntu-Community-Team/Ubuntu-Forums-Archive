---
title: "partition table help"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by KuroYoma on 2010-01-05
I was messing with my external harddrive and now gparted says that the entire drive in unformatted.   When I unplug it and plug it back in the partitions still pop up with all my data but gparted still says that there is nothing there.  I know that I messed up my partition table / MBR.  I am running a live cd of Ubuntu9.10  
Does anyone know what I can do to recover the partition table and not erase the partitions that still exist and are accessible?

---

### Post by gsmanners on 2010-01-06
I don't know if this will work, but you can try it:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by KuroYoma on 2010-01-06
Thank you.  Actually that gave me some of the information i needed to finish recovery.  I am in class now but afterwords I will try testdisk and let you know how it went.  Thank you again.

---EDIT---

I was able to use testdisk and locate the beginning sectors and end sectors of my partitions.  I used my basic knowledge of my partition setup and was able to use fdisk on my archlinux live cd to setup a new partition table.  All is well except one thing.  I can't find a hex number that represents hfs or hfs+ for a OSX partition type.  So right now i locked that partition so that I can get the filesystem type set properly.  

So that is my next question.  How do I set the filesystem type on a existing partition.  Or does anyone know what hex number represents the OSX filesystem types.  I see some of the options are like "Darwin *"  and I know Mac OSX runs on the Darwin Kernel and tools so would that work?

---

### Post by mikechant on 2010-01-06
> I can't find a hex number that represents hfs or hfs+ for a OSX partition type.

I would try x'AF' for hfs/hfs+. 
x'A8' and X'AB' are also for OS X but appear to be for UFS and boot partitions.

Have a look at this:
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)
and this
[http://www.sysresccd.org/Sysresccd-Partitioning-EN-Partitions-attributes#Partition_identifiers](http://www.sysresccd.org/Sysresccd-Partitioning-EN-Partitions-attributes#Partition_identifiers)

They seem to agree!

---

### Post by KuroYoma on 2010-01-07
Thanx.  For some reason I did not see that in my list.  Hopefully my disk of ArchLinux is not to old. It really shouldnt be.  I will try it and get back to you to let you know how it went thanx.

--EDIT--

IT worked!!!   I still couldnt see "af" as an option in the list I had but i typed that in anyways and it worked.  Using testdisk to locate my partitions start and end cylinders and fdisk to write a new partition table and define the filesystem type. WOOT.  All data is recovered.  Thanks for all your help

---

