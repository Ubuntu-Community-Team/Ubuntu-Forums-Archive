---
title: "external hard drive not reconized by computer"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by computerguts on 2010-01-24
I have a WD 1TB hard drive and it is not reconized by my computer that is operating ubuntu linux 9.10 
I typed in the command sudo fdisk -l
these are the results 

porter@porter-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 256 MB, 256901120 bytes
16 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         980      250864    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(978, 15, 32) logical=(979, 15, 32)
porter@porter-desktop:~$ 



what is the prolbem and how can I fix it ?

---

### Post by Mariane on 2010-01-24
Unplug it and plug it back in again. 
Just after you plug it back in type

dmesg | tail

and retype it until you see a line looking something like:

sdc:sdc1

Then type

cd /media
sudo mkdir disk

Then you type

sudo mount /dev/sdc1 /media/disk

But ONLY if you had sdc1 as a result before. Maybe you had something different, for example sdb:sdb1, in which case you replace sdc1 by sdb1. 

This is manually mounting the hard disk, so if you do this it is better to manually unmount it before unplugging it or turning off the computer. To unmout:

sudo umount /dev/sdc1

With the same remark concerning sdc1 which could be sdb1 or something. 

The contents of your external hard disk will be accessible in /media/disk

Mariane

---

### Post by llamabr on 2010-01-24
That's good advice to get it working, but doesnt' solve the problem.

Does it mount if you have it plugged in when you turn the machine on?  And what error does it give when you plug it in.

Also, it might help to see the output of:

```
dmesg | tail
```

---

### Post by computerguts on 2010-01-24
this is the output of the command dmesg|tail

porter@porter-desktop:~$ dmesg|tail
[ 4042.825253] scsi 3:0:0:0: Direct-Access     Ut163    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 4042.825841] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 4042.842727] sd 3:0:0:0: [sdb] 501760 512-byte logical blocks: (256 MB/245 MiB)
[ 4042.843593] sd 3:0:0:0: [sdb] Write Protect is off
[ 4042.843598] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 4042.843602] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4042.849095] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4042.849105]  sdb: sdb1
[ 4042.914346] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4042.914355] sd 3:0:0:0: [sdb] Attached SCSI removable disk
porter@porter-desktop:~$

---

### Post by halitech on 2010-01-24
Do you also have a 256meg thumbdrive plugged in? Only devices I'm seeing are your Internal 80gig drive and a 256meg drive which to me looks like a thumbdrive. 

Another thought, open up Partition Editor and see if the drive is partitioned properly. Its possible that all Ubuntu is seeing is the Windows partition that most WD My Books seem to have to hold the softwaer they use to back up your computer.

---

### Post by Mariane on 2010-01-25
This is strange. It seems you have a 256MB hard disk attached and not a 1TB hard disk. Anyway it is seen on sdb1 so it can be mounted and investigated. 

I would suggest you mount it like I said and then type
df -h

Mariane

---

### Post by computerguts on 2010-01-25
thanks

---

### Post by LuisGMarine on 2010-01-25
I had a similar problem with my WD passport hard drives.  I gave up trying to fix it on Linux.  What I did was booted up my windows XP partition, downloaded the formatting tool from WD website and restored it that way, after that for some reason Linux was able to see it.

I'm currently about to try this out for my other 2 hard drives that Linux can't seem to reformat. Best of luck!

---

### Post by computerguts on 2010-01-25
thanks, I will see if this is a solution

---

### Post by halitech on 2010-01-25
did you try any of the things suggested previously? If you did, it would help us if you tell us what the results were so we know what worked and what didn't for future issues people may have.

---

### Post by computerguts on 2010-01-25
the dmesg|tail command let me see the external hard drive but it would not let me mount if for some reason. I think it was an unformated drive. I showed no information about the drive except for the number. The results for the command are posted above.

---

### Post by halitech on 2010-01-25
if the drive is unformated then open Partition Editor and format the drive.

---

### Post by computerguts on 2010-01-25
LuisGMarine

what do you mean by formating tool, I don't see one avliable

---

### Post by computerguts on 2010-01-25
do you mean the source code ?

---

### Post by halitech on 2010-01-25
System - Admin - Partition Editor (otherwise known as Gparted)

---

