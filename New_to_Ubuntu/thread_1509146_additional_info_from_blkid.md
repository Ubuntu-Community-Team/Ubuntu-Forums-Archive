---
title: "additional info from blkid"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by harry003 on 2010-06-13
Let's start flogging a new horse, if you guys aren't ready to strangle me.

Check this out:

harry@hubuntu:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="7004DB5704DB1EC2" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="FA10DBD910DB9AC9" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="BC6C0A906C0A459C" TYPE="ntfs" 
/dev/sda5: UUID="b9d214c4-82e1-42bb-acce-41fda367689a" TYPE="ext4" 
/dev/sda6: UUID="3a6f3d1a-e01b-406e-8ec9-06b37c1c5e12" TYPE="ext4" 
/dev/sda7: UUID="7565bd5c-5610-4ed3-9ba5-e95f276aadc5" TYPE="swap" 
harry@hubuntu:~$ 

I would like to make a little chart, just for my own sake, about the names, sizes, misc info about these partitions, as Linux sees them.

I bought this laptop with Windows 7 pre-installed. I think the first partition is Vista but I have no idea why and would like to eliminate it. (I never see that "POSERVICE" anywhere else) I don't really know what the other NTFS is but "Acer" is the main bulk of my Windows hard drive about 190GB+ with both OS and data. 

I created the last 3 partitions from within Windows device manager, then booted into Live CD and formatted them from there. No idea what happened to 4, if it ever existed.

sda5 is my big 20GB Ubuntu data drive (/home as you so graciously informed me)
sda6 is my smaller 10GB Ubuntu OS drive (/ as I now know)
sda7 is my 10GB swap file.

I don't know how to get the Windows partition info from device manager without rebooting, but I will get that when I do.

Is there some nifty way to get all this in one place with details?

thanks

---

### Post by patchwork on 2010-06-13
I'm not sure about getting it all in one place with details in one fell swoop, but you can run
```
sudo fdisk -l
``` to see more information on each of your drives and partitions, including sizes, to add to what info you already have.

---

### Post by harry003 on 2010-06-13
Thanks, that tells me

harry@hubuntu:~$ sudo fdisk -l
[sudo] password for harry: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5b0ef8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       25302   190546210    7  HPFS/NTFS
/dev/sda4           25303       30402    40960001    5  Extended
/dev/sda5           27852       29127    10239258   83  Linux
/dev/sda6           25303       27852    20481024   83  Linux
/dev/sda7           29127       30402    10238976   82  Linux swap / Solaris

Partition table entries are not in disk order
harry@hubuntu:~$ 

Now I am really curious about 2 & 4

---

### Post by patchwork on 2010-06-13
sda4 is the 'cabinet', if you will, that is holding sda5, sda6, and sda7.  Since there is a limit to the number of primary partitions each drive can contain, sometimes one creates logical partitions residing in the primary partition.  sda4 is the primary partition, and the logical partions 5, 6, and 7 are in that primary partition.

This can be seen by looking at the block start and end for sda4 and each of the logical partitions.

It seems that your drive has something similar going on in partitions 1, 2, and 3, though the numbers don't quite jive the way I'd expect (but I have no experience with windows post 3.1).  sda2 seems to be a 10gb partition that contains the boot loader and, I'm assuming, core files.  sda3 seems to be a data partition ( your 190gb partition).

**I'm not the best at this stuff, so I'd wait for confirmation from someone more knowledgeable before you pull your hair out.**

---

### Post by Ozymandias_117 on 2010-06-13
> **harry003 said:**
> Let's start flogging a new horse, if you guys aren't ready to strangle me.

Check this out:

harry@hubuntu:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="7004DB5704DB1EC2" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="FA10DBD910DB9AC9" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="BC6C0A906C0A459C" TYPE="ntfs" 
/dev/sda5: UUID="b9d214c4-82e1-42bb-acce-41fda367689a" TYPE="ext4" 
/dev/sda6: UUID="3a6f3d1a-e01b-406e-8ec9-06b37c1c5e12" TYPE="ext4" 
/dev/sda7: UUID="7565bd5c-5610-4ed3-9ba5-e95f276aadc5" TYPE="swap" 
harry@hubuntu:~$ 

I would like to make a little chart, just for my own sake, about the names, sizes, misc info about these partitions, as Linux sees them.

I bought this laptop with Windows 7 pre-installed. I think the first partition is Vista but I have no idea why and would like to eliminate it. (I never see that "POSERVICE" anywhere else) I don't really know what the other NTFS is but "Acer" is the main bulk of my Windows hard drive about 190GB+ with both OS and data. 

I created the last 3 partitions from within Windows device manager, then booted into Live CD and formatted them from there. No idea what happened to 4, if it ever existed.

sda5 is my big 20GB Ubuntu data drive (/home as you so graciously informed me)
sda6 is my smaller 10GB Ubuntu OS drive (/ as I now know)
sda7 is my 10GB swap file.

I don't know how to get the Windows partition info from device manager without rebooting, but I will get that when I do.

Is there some nifty way to get all this in one place with details?

thanks

sda1 is most likely a recovery partition, used to reinstall Windows in case of failure. A lot of companies are doing this to save the price of a DVD disk with Windows on it.

sda2 was made by Windows during installation. I have no idea what it is for, so I've never messed with it.

sda3 would be your Windows 7 partition

sda4 A hard drive can only have 4 primary partitions, so to get around that, you can make one an extended partition which can then contain an unlimited Logical partitions. So, as patchwork called it, it's a "container" for the rest of your partitions.

sda5, 6, and 7 you seem to know what they are :)

---

### Post by bcbc on 2010-06-13
sda2 is the windows 7 boot partition. Given free reign, windows 7 will create a separate boot partition. If there is an existing windows installed it will put it's boot files on that one. Windows always boots the partition marked with the boot flag.

---

