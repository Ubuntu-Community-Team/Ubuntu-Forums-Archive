---
title: "How to fix a partition table"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by Edward in CT on 2011-04-22
I want to expand my Linux partition in Ubuntu 10.04 but GParted doesn't even see my existing partitions and only reports the presence of my entire hard drive.  It seems some of my disk geomety is wrong.  Can I fix this and recover what is already stored on the partiton?

---

### Post by oracle2b on 2011-04-22
I would suggest backing up and starting from scratch by formating if you suspect the disk geometry to be erroneous.

---

### Post by srs5694 on 2011-04-22
"Disk geometry" is pretty close to useless today; the CHS values used in years past top out at about 8 GB, so for everything bigger than that, only the LBA values are used.

Chances are you've got a minor partition table problem, such as a mis-sized extended partition. Such problems tend to make GParted report an empty drive, just as you say. If this is the problem, my [FixParts](http://www.rodsbooks.com/fixparts/) program will fix it. If you want a more certain diagnosis, run the following command:

```

sudo fdisk -lu

```

Note that's a lowercase letter "L", not a digit "1", in "-lu". Post the result here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to keep it legible. I or somebody else will be able to determine if my hypothesis is correct.

---

### Post by Edward in CT on 2011-04-23
Thanks.  Here is the results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    25173854    12586896    7  HPFS/NTFS
/dev/sda2        25173855    25382699      104422+   7  HPFS/NTFS
/dev/sda3        25382700   103521364    39069332+   7  HPFS/NTFS
/dev/sda4       103521411   312592769   104535679+   f  W95 Ext'd (LBA)
/dev/sda5       103522304   310550527   103514112   83  Linux
/dev/sda6       310552578   312576681     1012052   82  Linux swap / Solaris




What do you think???

---

### Post by oldfred on 2011-04-23
Fixparts is srs5694's tool that he developed that simplifies the solution.

Your drive says it is smaller than the extended partition.
Drive: 312581808 sectors
  sda4: 312592769

You need to back up partition table and copy it to another device just in case.

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

Fixparts - Repair broken partition tables
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by srs5694 on 2011-04-23
I concur with oldfred; your extended partition is too big for the disk, which is causing the problem. FixParts should deal with it. Check its Web page for complete instructions. Be aware that the Web page is quite verbose, in the interests of completeness; the actual repair will take a minute or less, even with backing up the partition table.

---

### Post by Edward in CT on 2011-04-24
srs5694 and oldfred:

I downloaded, installed, and used FixParts which worked perfectly.  I can now launch GParted and change the size of my Linux partition.  Thanks for all your  work and help.  I read the tutorial which I didn't fully understand (I'm a total beginner) but caught on enough to be able to use your brilliant piece of software.  I think it's impressive that I not only get help from guys who know Linux inside out, but who themselves wrote the code to fix my exact problem.   Linux rocks.

Thanks again
Ed

---

