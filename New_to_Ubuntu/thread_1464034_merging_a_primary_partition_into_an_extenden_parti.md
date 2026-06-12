---
title: "merging a primary partition into an extenden partition"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by Can Ozan on 2010-04-27
Hello, i want to install windows xp besides my win7 and ubuntu, but i've already 3 primary partitions, and 1 extended partition with ubuntu 10.04 beta. So i want to merge one of these primary partitions into my extended partition, so that i can install windows xp on a primary partition.

---

### Post by srs5694 on 2010-04-27
That could be tricky. Could you please post either the output of "sudo fdisk -l" or a screen shot of GParted showing your current partition layout?

---

### Post by mechro on 2010-04-27
If you "merge" one of the primary partitions with the extended partition then you'll have 2 primary partitions and 1 extended partition. Is that your intention?

---

### Post by Mark Phelps on 2010-04-28
> **Can Ozan said:**
> ... So i want to merge one of these primary partitions into my extended partition ...
As far as I know, you can't put a Primary partition INSIDE an Extended partition.  Those have to be Logical partitions.

And, I don't believe that you can install MS Windows to a Logical partition.

---

### Post by srs5694 on 2010-04-28
> **Mark Phelps said:**
> As far as I know, you can't put a Primary partition INSIDE an Extended partition.  Those have to be Logical partitions.

Partitions are just contiguous areas of a hard disk. It's theoretically possible to delete the primary partition, expand the extended partition to cover its area, and create a logical partition that covers the same area as the original primary partition. This will effectively do what Can Ozan is asking. In practice, though, this might not work, or at least it might require additional steps, such as shrinking another partition or moving one or more partitions, because of issues such as the need for at least one unallocated sector immediately before each logical partition and the need for all logical partitions to be contiguous. That's why I asked Can Ozan for the "sudo fdisk -l" output; that will reveal how the partitions are currently laid out and how difficult it will be to make these adjustments.

> And, I don't believe that you can install MS Windows to a Logical partition.

True, but with one current Windows partition and three current primary partitions, chances are at least one of the primary partitions is not a Windows installation partition. That said, the conversion may still be difficult or impractical for the reasons I've just outlined.

---

### Post by Can Ozan on 2010-04-28
First of all, thank you for your interest. I have solved my problem by deleting one primary partition which was just after my extended partition, and I just resized my extended partition to cover the area deleted. I have done all of these with gparted. So now I have 2 parimary partitions, and 1 extended partition.
   But now I have another big problem. I was trying to shrink one of my primary partitions with windows 7 on it, in order to make a 3rd primary partition for windows xp. 
   I tried to use parition magic 8, but then everything went off! This means windows has shut down and every time I want to boot to windows 7, it reboots. 
   The partition concerned was 196 GB, and now it seems to be 30 GB, and the rest is unallocated. I think the partition magic changed something and now windows 7 cannot find some necessary files to boot. 
   When I run Gparted, all my hard disk seems unallocated, but it is not true because i can run ubuntu.
   Here are the results of sudo fdisk -lu
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5f39656f

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/sda1   *        2048    64276064    32137008+   7  HPFS/NTFS
/dev/sda2        64264192   475893494   205814651+   7  HPFS/NTFS
/dev/sda4       475893556   976768064   250437254+   f  W95 Ext'd (LBA)
/dev/sda5       475893558   482030324     3068383+  82  Linux takas / Solaris
/dev/sda6       482030388   537326054    27647833+  83  Linux
/dev/sda7       537326118   976768064   219720973+   7  HPFS/NTFS


and sudo sfdisk -d /dev/sda

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 64274017, Id= 7, bootable
/dev/sda2 : start= 64264192, size=411629303, Id= 7
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=475893556, size=500874509, Id= f
/dev/sda5 : start=475893558, size=  6136767, Id=82
/dev/sda6 : start=482030388, size= 55295667, Id=83
/dev/sda7 : start=537326118, size=439441947, Id= 7


so can you please help me recover my windows 7? I have also a windows 7 cd, which is uncapable of repairing itself!!!

---

### Post by Can Ozan on 2010-04-28
Also this is not it, i'm continuing to messing up my system!!! I used a program called testdisk, and now I can boot into win7, which is again 196GB, but now it seems that i have lost all my other info, including my partition with linux, which is standing right there in the previous post.
   The new outputs for fdisk is


 Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xebe0bfdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    64264191    32131072    7  HPFS/NTFS
/dev/sda2        64264192   475889663   205812736    7  HPFS/NTFS
/dev/sda3       475893495   482110630     3108568   82  Linux swap / Solaris
/dev/sda4       482110650   976784129   247336740    f  W95 Ext'd (LBA)
/dev/sda5       507461220   562756883    27647832   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000405d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)



and for sudo sfdisk -d /dev/sda

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 64262144, Id= 7, bootable
/dev/sda2 : start= 64264192, size=411625472, Id= 7
/dev/sda3 : start=475893495, size=  6217136, Id=82
/dev/sda4 : start=482110650, size=494673480, Id= f
/dev/sda5 : start=507461220, size= 55295664, Id=83



Can anyone please help me recover my lost data? I don't want to believe that i have formatted my hard disk, and i want to beleive that i have just changed the start and end sectors for my partitions, so that just by forcing my computer to read them as on my previous post (for /dev/sda3,4,5,6,7,  not for /dev/sda1,2), i can recover my data.

 Even fdisk gives me these outputs, gparted still insists on seeing my entire hard disk as unallocated.

---

### Post by srs5694 on 2010-04-28
This is ***very risky,*** but it might work:

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 2048, size= 64262144, Id= 7, bootable
/dev/sda2 : start= 64264192, size=411625472, Id= 7
/dev/sda4 : start=475893556, size=500874509, Id= f
/dev/sda5 : start=475893558, size= 6136767, Id=82
/dev/sda6 : start=482030388, size= 55295667, Id=83
/dev/sda7 : start=537326118, size=439441947, Id= 7

```

I've combined your two working configurations to create the above. Save it in a file (say, parts.txt) and pass it to sfdisk:

```

sudo sfdisk /dev/sda < parts.txt

```

You may need to add a "-f" parameter between "sfdisk" and "/dev/sda" if sfdisk sees something it doesn't like about the partition definitions. I ***strongly*** recommend that you back up your working Windows installation before you try this, with or without the "-f" parameter. (You can use ntfsclone or a Windows native tool for the job.)

If it's successful, both systems will become accessible, and you can then use fdisk, GParted, or some other tool to make additional changes. If it's not successful, there's a chance that it'll do further (even irreparable) damage, since each logical partition (those numbered 5 and above) requires a 1-sector data structure immediately before its start. If the logical partition definitions are incorrect, these data structures could damage parts of the preceding partitions in ways that would be hard to predict.

Good luck!

---

### Post by Can Ozan on 2010-05-04
I will not be home for about 2 months, so i cannot try what you have suggested. But thank you very much. When i return home, i will surely give it a try, after backing up my data.
   And about your concerns with space required before logical partitions, i think that will not be a problem because the values i gave you were being used without problems a week ago. 
   
    I will give the details as soon as i have something to write.

---

### Post by Animal X on 2010-05-04
i have encapsulated extra volumes (up to 14) inside the extended partition housing my ubuntu with 3 other primary partitions in play, but it became unstable or something during an install of windows and i wiped out most of the extra partitions losing lots of personal data, but it didn't disturb the other OS's.

---

### Post by srs5694 on 2010-05-04
> **Animal X said:**
> i have encapsulated extra volumes (up to 14) inside the extended partition housing my ubuntu with 3 other primary partitions in play, but it became unstable or something during an install of windows and i wiped out most of the extra partitions losing lots of personal data, but it didn't disturb the other OS's.

It sounds like something damaged one of the links in the chain of logical partitions. Some background: Logical partitions are defined using what's known as a *linked list* data structure, meaning that the first logical partition's definition includes a pointer to the next one, which includes a pointer to the third, and so on. If one of these pointers is damaged, then all subsequent partitions will be lost. Such accidents are rare, but they do happen.

---

### Post by Can Ozan on 2010-06-28
Thank you everyone, I got my computer back in life with all my partitions. I just had to force my computer for the partition table. Thanks a lot.

---

