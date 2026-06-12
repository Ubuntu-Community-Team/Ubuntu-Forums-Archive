---
title: "Resizing /home and / and resizing NTFS"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-02-07
At boot I see a message that /Windows is about to run out of space. I want to enlarge the Windows 7 partition. See the attached screenshot.

GParted spent 4 hours this morning, moving/resizing /sda5 by (approx) 11 gig, making it now: 303.65 gig.

The new space, shown in the screenshot as sda7 is sitting "in between" the / and the /home directories. In between /sda4 and /sda5. I now want to increase the size of /

and then move that increased space to the /windows (sda2) partion.

fdisk -l says:

[COLOR="DarkSlateGray"]Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+   7  HPFS/NTFS
[COLOR="Red"]/dev/sda2              13        4462    35736576    7  HPFS/NTFS[/COLOR]
/dev/sda3            6503       48641   338481517+   5  Extended
/dev/sda4   *        4463        6502    16386300   83  Linux
/dev/sda5            7983       47621   318400267+  83  Linux
/dev/sda6           47622       48641     8193118+  82  Linux swap / Solaris
/dev/sda7            6503        7982    11888037   83  Linux

Partition table entries are not in disk order[/COLOR]

My question is, after adding to the size of / how do I move what is at the beginning of / , so that grub2 looks for it's info, it finds it. That is, how do I add to / , then move the unused space to the front of / safely?

---

### Post by oldfred on 2011-02-07
Delete sda7, it is unallocated you are moving around.

I hope you have good backups of all your data. You will be moving root.

Move the left end of the extended partition right to move the unallocated out of the extended partition. Then you can move root right, then move the left side of win to include the unallocated. If Vista or 7 use windows tools to adjust the windows partition. I would do in steps and check that systems boot ok. You may have to reinstall grub if the partition is moved, but moving should not change UUIDs and cause you to have to update fstab & grub with new UUIDs.

Windows needs 20 to 30% free space or it slows or stops working. I might suggest if you are using both windows & Linux you may want some or most of your data in a shared NTFS partition. I do not like writing into a foreign system as that can lead to problems. Reading is ok and if repairing then you have to write into the windows partition.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

I always prefer to keep system partitions small and have all my data in data partitions, both for windows & Linux.

---

### Post by Mark_in_Hollywood on 2011-02-07
oldfred:

Please forgive my ignorance, but when you write:

"Move the left end of the extended partition right to move the unallocated out of the extended partition. Then you can move root right, then move the left side of win to include the unallocated. If Vista or 7 use windows tools to adjust the windows partition."

I have no idea of what "the extended partion" is. And I've re-read that paragraph 7 times now.

Could I trouble you to reply in terms of partitions by their numbers, such as: sda5? Also, I cannot seem to grasp what you mean by "to move the unallocated out of the extended partition". I looked at the flags on the partitions to see if "extended" was used, but I cannot grok what you are saying.

---

### Post by oldfred on 2011-02-07
[COLOR=DarkSlateGray]From your post:
/dev/sda3            6503       48641   338481517+   5  Extended

Please see instructions on using gparted and resizing partitions.


[/COLOR]

---

