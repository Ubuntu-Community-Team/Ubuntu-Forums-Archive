---
title: "Unable to understand how to rescue grub. Please Help!"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Rushyang on 2010-10-11
Hey guys,

I was on.. Dual Boot --> Windows 7 x64 Ultimate + Lucid Lynx x86

I was trying to install 10.10 brand new installation. I boot into Windows and from the Partitions software, I formatted Lucid Lynx Partition. Then installed 10.10 but wasn't able to install NVIDIA drivers and I couldn't bare it cause My Graphic Card FAN noise without drivers drives me insane. So I again installed 10.04 on the same partition..

But when I boot my Primary HDD, There is a screen comes saying...

> Grub Rescue >None commands work in that. I tried inserting 10.04 Disk but unable to understand how to restore grub. 

I booted into Live USB and tried 

```
 
root(hd0,1)
find /boot/grub/stage1 
setup(hd0)

```But none command works.. 

Here is my fdisk ... 

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbfd1f177

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11749    94371840    7  HPFS/NTFS
/dev/sda2           11749       46996   283115520    7  HPFS/NTFS
/dev/sda3           46996       60802   110896128    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f656

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       11218    38909430   83  Linux
/dev/sdb3           11219       19457    66179737    f  W95 Ext'd (LBA)
/dev/sdb5           11219       11473     2048256   82  Linux swap / Solaris
/dev/sdb6           11474       17937    51921920    7  HPFS/NTFS
/dev/sdb7           17938       19457    12209368+   7  HPFS/NTFS

Disk /dev/sdc: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d319a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         489     3921888+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(487, 254, 63) logical=(488, 65, 25)

Please help guys! ASAP.

---

### Post by celticbhoy on 2010-10-11
10.04 uses grub2, the commands you tried are for the old grub.

Do you have a live disk you can use?

---

### Post by Rushyang on 2010-10-11
> **celticbhoy said:**
> 10.04 uses grub2, the commands you tried are for the old grub.

Do you have a live disk you can use?

Yes, at the moment I have both, Live USB and Live CD to boot.

---

### Post by celticbhoy on 2010-10-11
Good.

Boot into your live disk and follow the instructions on this link, they are simple to follow.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by Rushyang on 2010-10-11
Man, that helped me out of my misery. Can I know how to perform a brand new installation on the same partition without affecting GRUB2  ?

---

### Post by celticbhoy on 2010-10-11
If you are going to install 10.04, or 10.10 on the partition they will just re-install grub2.

I would advise that you select the option to format the partition, when the installer is running.

---

### Post by Rushyang on 2010-10-11
Alright, that would suffice for now. Thanks a ton for your help. :)

---

