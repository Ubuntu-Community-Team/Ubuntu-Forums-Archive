---
title: "Flash drive and pictures"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by psyk117 on 2010-09-08
Every time I put pictures onto my flash drive, the become all funky, off colored or just flat gray. What is causing this? How can it be fixed?

---

### Post by Naitsirhc Hsem on 2010-09-08
do you eject or safely remove the drive before you unplug it?

---

### Post by psyk117 on 2010-09-08
> **Naitsirhc Hsem said:**
> do you eject or safely remove the drive before you unplug it?
I sometimes do, and I sometimes don't...

---

### Post by Slim Odds on 2010-09-08
> **psyk117 said:**
> Every time I put pictures onto my flash drive, the become all funky, off colored or just flat gray. What is causing this? How can it be fixed?

You give absolutely no information about how you do it. How do you expect us to troubleshoot that?

How are you transferring the files?

---

### Post by psyk117 on 2010-09-08
> **Slim Odds said:**
> You give absolutely no information about how you do it. How do you expect us to troubleshoot that?

How are you transferring the files?

I copy and paste them to the drive.

---

### Post by Naitsirhc Hsem on 2010-09-08
When you remove it while it is still blinking, all of the data has not been copied, use the eject or safely remove options. a  few extra seconds of caution can save you hours of debuging

---

### Post by psyk117 on 2010-09-08
> **Naitsirhc Hsem said:**
> When you remove it while it is still blinking, all of the data has not been copied, use the eject or safely remove options. a  few extra seconds of caution can save you hours of debuging

It still happens. I have no clue what to do. I did the safely remove drive after I copied some test pictures onto the drive. some are perfectly fine. others are screwed up.

---

### Post by bredman on 2010-09-08
You may have a faulty disk which is corrupting the files.

Try using a utility such as testdisk to check the health of the disk, use the following command to install

sudo apt-get install testdisk

---

### Post by psyk117 on 2010-09-08
> **bredman said:**
> You may have a faulty disk which is corrupting the files.

Try using a utility such as testdisk to check the health of the disk, use the following command to install

sudo apt-get install testdisk

installed, now how do I run it? I apologize for being so green at this.

edit: I figured it out.

---

### Post by bredman on 2010-09-08
I forgot to tell you how to use testdisk...

Enter the command
sudo testdisk

Select "Analyse"
Select "Quick search"
Point to what looks like your external drive (probably /dev/sdb Linux) and press Enter
Select "Deeper Search"

If several disks are visible, you can use the size of the disk to guess which is which. For example a 2GB flash drive would look like
Disk /dev/sdb - 2 GB / 2 GiB

---

### Post by psyk117 on 2010-09-08
> **bredman said:**
> I forgot to tell you how to use testdisk...

Enter the command
sudo testdisk

Select "Analyse"
Select "Quick search"
Point to what looks like your external drive (probably /dev/sdb Linux) and press Enter
Select "Deeper Search"

If several disks are visible, you can use the size of the disk to guess which is which. For example a 2GB flash drive would look like
Disk /dev/sdb - 2 GB / 2 GiB
ok. got it.
oh man... this is going to be a doozie
these partitions show up:
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition

now how do I make it so that there is only one?

---

### Post by philinux on 2010-09-08
> **psyk117 said:**
> ok. got it.
oh man... this is going to be a doozie
these partitions show up:
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition

now how do I make it so that there is only one?

Use System>admin>disk utility and format the flash drive. Assuming there's nothing important on it.

---

### Post by psyk117 on 2010-09-08
> **philinux said:**
> Use System>admin>disk utility and format the flash drive. Assuming there's nothing important on it.

that didn't work. still the same options.

---

### Post by bredman on 2010-09-08
Sorry, forgot to tell you to select an Intel PC disk.

---

### Post by psyk117 on 2010-09-08
> **bredman said:**
> Sorry, forgot to tell you to select an Intel PC disk.

Disk /dev/sdb - 8053 MB / 7680 MiB - CHS 1023 248 62

Warning: the current number of heads per cylinder is 248
but the correct value may be 16.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.


what can you make of this?

---

### Post by bredman on 2010-09-08
Ignore warnings like this. Flash drives often do things which would be very unlikely for a physical hard disk. Go all the way to a deeper search.

Sorry, got to leave now. Wish you luck...

---

### Post by psyk117 on 2010-09-08
> **bredman said:**
> Ignore warnings like this. Flash drives often do things which would be very unlikely for a physical hard disk. Go all the way to a deeper search.

I got this:

     Partition                  Start        End    Size in sectors

 1 * FAT32                    0   1  1  1021 247 62   15714210 [Ark]

---

