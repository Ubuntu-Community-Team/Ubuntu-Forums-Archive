---
title: "How to view separate hard drives"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by kroni_hunter on 2010-09-27
I have 3 hard drives in my computer, but Ubuntu doesn't seem to show any of them in the computer section.  It also only shows one of my two optical drives.  Am I missing some specific drivers or is there some special way to access them?  I also cannot install the Support DVD that came with my Motherboard.  Total n00b here please help.

---

### Post by andrewthomas on 2010-09-27
post the output of 

```
sudo fdisk -l
```in the terminal

---

### Post by kroni_hunter on 2010-09-27
Where is the terminal?

---

### Post by Tibuda on 2010-09-27
> **kroni_hunter said:**
> I have 3 hard drives in my computer, but Ubuntu doesn't seem to show any of them in the computer section.  It also only shows one of my two optical drives.  Am I missing some specific drivers or is there some special way to access them?
I don't really know, but I'd suggest you to install [gparted](apt://gparted) and try to see the drives in the partition manager.

> I also cannot install the Support DVD that came with my Motherboard.
It probably only contain Windows drivers. If your wireless card is working fine, and you got a nice resolution, you don't need them.

---

### Post by Tibuda on 2010-09-27
> **kroni_hunter said:**
> Where is the terminal?

Applications > Accessories

---

### Post by kroni_hunter on 2010-09-27
Ok, i found the terminal and I typed in that code, but then it asks for my password but it will not allow me to type it in...Nothing else happens.

---

### Post by Tibuda on 2010-09-27
> **kroni_hunter said:**
> Ok, i found the terminal and I typed in that code, but then it asks for my password but it will not allow me to type it in...Nothing else happens.

while you type your password in a terminal, you have no visual feedback (no *), but it is working.

---

### Post by kroni_hunter on 2010-09-27
Thank you Tibuda.  This is my first time ever trying Ubuntu and I'm totally lost.  Even the how to guides don't make any sense to me.  Theres a message coming up saying that disks do not contain a valid partition table.  What do I do from there?

---

### Post by srs5694 on 2010-09-27
> **kroni_hunter said:**
> Thank you Tibuda.  This is my first time ever trying Ubuntu and I'm totally lost.  Even the how to guides don't make any sense to me.  Theres a message coming up saying that disks do not contain a valid partition table.  What do I do from there?

Do you mean that fdisk is returning that message? If so, please post the exact output of the "sudo fdisk -lu" command, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. Also, what type of computer do you have? (CPU, hard disk sizes, etc.) The fdisk tool doesn't understand all partition table types, and it's conceivable you've got something else, particularly if it's a Mac or some sort of exotic system.

---

### Post by kroni_hunter on 2010-09-28
It's a computer I built, using WD 2TB Internal Hard drives.  Here's the code:
```
 

]trippel@HOLYDEMON:~$ sudo fdisk -lu
[sudo] password for trippel: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1999.7 GB, 1999696297984 bytes
255 heads, 63 sectors/track, 243115 cylinders, total 3905656832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3905656831  1952827392    7  HPFS/NTFS
trippel@HOLYDEMON:~$ 


```

Also, I found that on the startup theres a message in the BIOS saying no hard disk detected.  I'm pretty sure its not a connection problem they are all secured to the PSU and a SATA line.

---

### Post by srs5694 on 2010-09-28
According to the fdisk output, you've got *four* (not three) disks:


[list=1]
[*]/dev/sda uses the GUID Partition Table (GPT) partitioning system, which fdisk doesn't understand, so it's still not clear what's on that disk in the way of partitions. I recommend you download and install [GPT fdisk (gdisk)](http://sourceforge.net/projects/gptfdisk/files/), type "sudo gdisk -l /dev/sda", and post those results here for analysis.
[*]/dev/sdb has no partition table -- at least, none that fdisk can understand.
[*]/dev/sdc has no partition table -- at least, none that fdisk can understand.
[*]/dev/sdd has a single NTFS partition that covers the whole disk.
[/list]


If you're certain you've got just three disks, then my guess is that something is causing one disk to show up twice (probably as /dev/sdb and /dev/sdc), but I'm not sure what could cause such a problem. Perhaps the output of dmesg would produce a clue -- scan it for messages relating to the four disk devices.

What do you believe *should* be on these disks? Should they all be partitioned, or is the lack of partitions on two disks to be expected?

The fact that you got a BIOS message about hard disks is also suspicious. That sounds like a hardware problem. Maybe you've got a bad cable, or the disk controller circuitry on the motherboard is damaged.

One approach to further debugging at this point is to simplify things. Unplug all but one of the hard disks and your boot device (presumably a CD/DVD drive) from the motherboard and try again. If that works better, shut down and start adding devices back until you get a failure. You can then try further adjustments, like removing other drives or swapping cables around, to try to isolate what's causing the failure.

---

