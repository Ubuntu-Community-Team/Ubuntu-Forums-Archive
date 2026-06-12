---
title: "Ubuntu Installer Doesn't Recognize Windows 7"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by TQBRFJOALD on 2010-12-27
I have been trying to dual boot Windows and Linux on my custom built barebone i7 2.67 ghz with windows 7 pro 64 bit, but every distro I try I have the same issue - the installer thinks there is nothing on my four HDs. In Windows, it considers the partition Windows is installed on to be one big partition (it is on all of my HDs) and (as far as I can see) doesn't even point out that it is on four HDs. Here is the "fdisk -lu" output on PartedMagic Terminal:```
Welcome - Parted Magic (Linux 2.6.35.7-pmagic)

root@PartedMagic:~# fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7549d38c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3907035135  1953516544    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7549d38c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  3907035135  1953516544    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 2038 MB, 2038431744 bytes
251 heads, 62 sectors/track, 255 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          64     3981311     1990624    c  W95 FAT32 (LBA)

```

but on partition editor on Parted Magic and on all of the Linux installers it says all four hard drives are 931.51 gigs (which makes no since), and they are all unallocated.

BTW - Dont worry about /dev/sde, thats just a flash drive.

Thanks

---

### Post by oldfred on 2010-12-28
Even the fdisk says it cannot see sdc & sdd. Do you have NTFS partition(s) on those drives?

Linux often will not work with NTFS partitions that need chkdsk, so that it does not damage it and prevent chkdsk from repairing it. I might try chkdsk first.

Do you have 4 copies of windows installed? Or just 4 NTFS partitions?

Were these drives ever set up in RAID. RAID leaves meta data on a drive that can interfer with non-RAID installs.

---

### Post by TQBRFJOALD on 2010-12-28
Yes I do have Raid. I have one big partition on all of those hard drives (so all of them combined makes up one partition) which is where Windows 7 is installed (so i only have one copy of windows). I will try chkdsk, ill report if it works. I have never fully completed a chkdsk (due to impatientness), so I guess I will. The thing is that I cannot see my HDs in Windows using Disk Management, its just a huge partition.
I know I am such a noob.

---

### Post by TQBRFJOALD on 2010-12-28
chkdsk didn't do anything. I restarted and tried linux mint - the installer just had volume 0 (the windows partition) and volume 1 (the raid partition). It said that both volumes had nothing on them. I went on GParted with the Mint livecd and it was the same as PMagic - 4 931.51 gig unallocated hard drives. So I understand the problem is raid, is it possible to install linux with raid?

---

### Post by oldfred on 2010-12-28
The newest LiveCD may work with RAID but I have usually seen the recommendation to use the alternative installer as it included the extra RAID drivers. Not sure about Mint, but I would doubt that that would normally be included as RAID is unusual on desktops.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by TQBRFJOALD on 2010-12-28
Thanks, Ill try out the alternate 64 bit

---

### Post by TQBRFJOALD on 2010-12-28
Doesn't recognize windows but it does recognize raid. So if i wanted to install ubuntu I would have to uninstall win 7. Oh well, I give up. thx anyway

---

### Post by Mark Phelps on 2010-12-29
> **TQBRFJOALD said:**
> Doesn't recognize windows but it does recognize raid. So if i wanted to install ubuntu I would have to uninstall win 7. Oh well, I give up. thx anyway

Don't give up so soon!

With all that drive space, surely you can spare some for Ubuntu!

Use the Win7 Disk Management utility to shrink the space allocated to Win7, leaving the remainder unallocated.

Then, see if the alternate CD can recognize that space.

---

### Post by TQBRFJOALD on 2010-12-29
alright

---

### Post by TQBRFJOALD on 2010-12-29
Didn't work. Same as always - doesn't recognize Windows and thinks its all free space. It doesn't recognize the partition table either. What I need is way to install Ubuntu with raid 0+1 without uninstalling Win 7

---

### Post by gabak on 2011-01-30
hi everyone
i have the same problem with windows 7
i think has something to do with some patch of windows 7 some update at affect purposely the partition.
i had a samsung notebook , and it saw the partition but when i tried to modified it did nt let me to add a new partition for ubuntu.
after several tries i choose to wipe off the whole hdd then i install windows 7 then right away ubuntu and it works great.
now in my personal pc i still have the same problem, but here it get worse and weird.
i boot with live cd and i choose to install it then i dont see any windows partition and it does nt let me to install it aside anythig cuz it simple does nt detect win7 now if i boot with live cd again and i choose try ubuntu then i see all my partiotion and all my folders. but when i doble click on the icon to install it and i should have the option to choose the hdd , i dont see any partition. !!!! that is super weird.
i think microsoft does nt want ppl to have other OS beside their own.

---

### Post by Mark Phelps on 2011-01-31
gabak:

Please do NOT hijack this thread.  The OP has RAID setup and that poses different problems than the usual installation difficulties.

It's hard enough to help one person with such problems.

When others hijack their threads with different problems, it just becomes confusing as to which suggestions affect which poster.

Please start your own thread.

---

### Post by Mark Phelps on 2011-01-31
> **TQBRFJOALD said:**
> Didn't work. Same as always - doesn't recognize Windows and thinks its all free space. It doesn't recognize the partition table either. What I need is way to install Ubuntu with raid 0+1 without uninstalling Win 7

I'm confused.  

In an earlier post, you said the alternate CD did recognize RAID but now, you're saying after you shrunk the Win7 OS partition it does not?

---

