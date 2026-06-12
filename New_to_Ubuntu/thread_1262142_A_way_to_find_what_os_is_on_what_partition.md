---
title: "A way to find what os is on what partition?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by kronos262 on 2009-09-09
So I was triple booting my PC when now I cannot boot windows or mac.
 
 
Ubuntu boots fine.
 
 
The order was Ubuntu, XP, Mac.
 
At least that is how I installed them.
 
 
I had Ubuntu and XP working fine with XP at
 
title Windows XP
root     (0,1)
Make active
chainloader + 1
 
 
but when I installed Mac, which I assumed would have been 0,2, now windows will not boot unless I run a bootcfg Rebuild in Recovery Console, 
 
but if I reboot I am getting a missing hal.dll.
 
One assumption is the boot.ini is wrong and has windows on the wrong partition, or GRUB has it on the wrong partition.
 
I haven't messed with it yet but I wanted to see what people may say first.

---

### Post by NinjaNumberNine on 2009-09-09
How can you install mac on a pc?

---

### Post by LowSky on 2009-09-09
Each OS uses a different type of file system.

Ubuntu uses EXT3 or EXT4
Windows USES FAT32 or NTFS
OS/X uses HFS+

open up gparted or run fstab to see the partitions.

---

### Post by kronos262 on 2009-09-09
> **LowSky said:**
> Each OS uses a different type of file system.
 
Ubuntu uses EXT3 or EXT4
Windows USES FAT32 or NTFS
OS/X uses HFS+
 
open up gparted or run fstab to see the partitions.
 
 
I figured I could use Live cd and gparted. I will do that. I saw it this morning before I went to Certification class so didn't have time.
 
 
Also mac on a PC.
 
Google, Youtube.
 
Here are some terms Iatkos, Ideneb, IPC
 
 
edit:
 
 
Also is there a command prompt in case gparted shows that it is still linux, xp, mac in that order

---

