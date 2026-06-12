---
title: "Power Failure, now weird permission troubles"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by ah pook on 2009-07-17
I had a power failure yesterday ( I know, use a UPS ) and now I'm having trouble with USB storage and Hard drives disappearing. I have a couple thumb drives which have always worked and now say
" You do not have permission to mount this volume" Plus my 500G
USB backup says the same thing, although I remember explicitly setting
the Owner to myself. 

Also, a 120G internal drive just disappeared. No sign of it anywhere, no matter where I look. 

I'm pretty stumped. any help would be greatly appreciated.

---

### Post by NightwishFan on 2009-07-17
A question before I help you. I was wondering where your username comes from. It sounds familiar.

To see if your disks are available, open a terminal and type:
```
sudo fdisk -l
```

This will show you the available partitions. Perhaps boot into recovery mode and run a fsck. You can do this in the kernel selection screen on GRUB. (The loader where you select your OS)

---

### Post by ah pook on 2009-07-17
Nightwishfan - 

Thanks for the help. the name comes from a William Burroughs book, 
Ah Pook is here, and Ah Pook also figures in the Western Lands Trilogy. It comes from the Mayan god of death and destruction...

Anyway, I'm at work, so I'm just collecting starting points for what to do when I get home...I already ran fsck from recovery mode, but to no avail... I'll continue asking for help in four hours or so when I'm home in front of the computer...

Thanks for the quick response. People on here are wonderful....

---

### Post by ah pook on 2009-07-17
so I got my 500 gig drive working, I have no idea how, but the Flip mino Hd 
camcorder is still giving me a "You are not ptivilged to mount the volume FLIPVIDEO" error. the 120 gig drive is gone, and probably dead, as far as I know, so let's not worry about that...

---

### Post by ah pook on 2009-07-17
this is the output of Fdisk-l the relavant part, anyway:
Disk /dev/sde: 2047 MB, 2047868416 bytes
248 heads, 62 sectors/track, 260 cylinders
Units = cylinders of 15376 * 512 = 7872512 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          11       80293+   0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(9, 254, 63) logical=(10, 111, 8)
Partition 1 does not end on cylinder boundary.
/dev/sde2              11         261     1919543+   b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(10, 0, 7) logical=(10, 111, 15)
Partition 2 has different physical/logical endings:
     phys=(248, 247, 62) logical=(260, 31, 61)
geo@geo-desktop:~$

---

### Post by NightwishFan on 2009-07-18
The flip video uses some sort of FAT filesystem I think. Make sure only one user has mounted it at a time. Other than that I do not have much advice.

---

