---
title: "Attempt to dual boot 10.1 with windows 7 resulsts in unusable partition"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Randy M on 2010-12-04
I tried to install 10.1 on a friends laptop today (HP Pavilion) from a  CD. I changed the partition size from the CD and the result was an  unusable partition. Nothing in the partitioning menu would make it  usable. Any suggestions on where I went wrong? When I installed on my  laptop (also an HP) there was a slider bar that selected where to divide  the existing dos partition. The next step was to finish the install.  Thanks for any help.

---

### Post by coffeecat on 2010-12-04
HP are notorious for using up the 4 primary partition allowance, which means you cannot add any partitions until you delete one and replace it with an extended partition. I'm guessing that when you say you have an 'unusable partition', you are seeing unallocated space in which the partitioner will not allow you to create a partition - because of the 4 primary partition limitation.

So that we can see what the situation actually is, and if my guess is right, boot up the live CD on your friend's  HP, open a terminal and post the output of:

```
sudo fdisk -lu
```

---

### Post by Randy M on 2010-12-06
Thanks, I'll get the information and post it here the next time I see him.

---

### Post by wilee-nilee on 2010-12-06
> **Randy M said:**
> Thanks, I'll get the information and post it here the next time I see him.

Besides the last command do this as well. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by Randy M on 2010-12-08
Here's the information. Thanks for any help.
====================
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x471a47b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   469159599   234375000    7  HPFS/NTFS
/dev/sda3       939626496   976560127    18466816    7  HPFS/NTFS
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)

Disk /dev/sdb: 2031 MB, 2031091712 bytes
63 heads, 62 sectors/track, 1015 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4dd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3964589     1982264    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2010-12-09
Yes, there are four primary partitions on the 500GB drive. That is the limit for a MBR partition table which is what Windows machines use. To be able to create more than 4 partitions, one primary has to be deleted after which you can create an extended partition in whatever (continuous) space is available. An extended partition is not used directly but is a virtual container for however many logical partitions you need.

The layout and sizes are as follows:

Partition 1 - sda1 - 208MB - most likely the Windows 7 boot partition.

Partition 2 - sda2 - 240GB - most likely the Windows C: partition which you have shrunk. You say you reduced it from the CD and that it was unusable. Do you mean that Windows became unbootable or that the resulting space was unusable?

Unallocated space between sda2 and sda3 of 240.9GB

Partition 3 - sda3 - 18.9GB - probably an OEM HP recovery partition.

Partition 4 - sda4 - 108MB - seeing as it's a FAT filesystem I would guess some sort of HP utility partition.

Before you do anything else I suggest you boot into Windows and prepare a set of HP recovery DVDs if your friend has not already done so. Also making a Windows 7 repair CD would be a good idea too, which you can do from inside windows 7. This is because your choice is between deleting sda3 or sda4. It would be a good idea to have a look in Windows Disk Management to see what those partitions really are before making the choice. Those are my assumptions above.

If you delete sda3, you will have about 260GB of continuous free space in which you can create an extended partition. If you delete sda4, you will have nearly 241 and the freed 108MB could be abandoned or sda3 moved to the right. Personally, I would abandon the 108MB because moving partitions runs the risk of something going wrong.

In addition to the above, there is also a 2GB sdb. Was a USB pendrive plugged in when you ran fdisk - perhaps a live Ubuntu USB?

---

