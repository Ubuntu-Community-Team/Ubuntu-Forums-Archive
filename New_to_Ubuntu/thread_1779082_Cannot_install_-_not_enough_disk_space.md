---
title: "Cannot install - not enough disk space"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by polandee on 2011-06-09
Hey, I'm posting from a computer running the trial version of Ubuntu. I just got a new hard drive, and was expecting to install ubuntu, but it says I need at least 4.4 Gb of memory, while I have an entire hard drive. Does anyone know why it would think that I don't have enough memory?

---

### Post by -kg- on 2011-06-09
Open up a terminal window and run the following command:

```
sudo fdisk -l
```

That will show us what you're dealing with as far as hard drives and hard drive space.

---

### Post by alphacrucis2 on 2011-06-09
> **polandee said:**
> Hey, I'm posting from a computer running the trial version of Ubuntu. I just got a new hard drive, and was expecting to install ubuntu, but it says I need at least 4.4 Gb of memory, while I have an entire hard drive. Does anyone know why it would think that I don't have enough memory?

Perhaps your hard drive is already formatted so ubuquity doesn't think there is any space available.

---

### Post by polandee on 2011-06-09
That doesn't do anything. It doesn't cause an error, it just doesn't do anything.

---

### Post by -kg- on 2011-06-09
OK, are you absolutely sure the hard drive is hooked up correctly?  That command should give you a list of the hard drives connected to your computer.  The following is the output of that command on my laptop:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        9409    74033152    7  HPFS/NTFS
/dev/sda3            9409       10531     9020081+   7  HPFS/NTFS
/dev/sda4           10532       12161    13092975    5  Extended
/dev/sda5   *       10532       12161    13092864   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117216225+   f  W95 Ext'd (LBA)
/dev/sdb5               1        2439    19585012    7  HPFS/NTFS
/dev/sdb6            2440        5652    25808391    7  HPFS/NTFS
/dev/sdb7           14193       14593     3221001   82  Linux swap / Solaris
/dev/sdb8            7664       13361    45769153+  83  Linux
/dev/sdb9           13362       14192     6674976   83  Linux
/dev/sdb10           5653        7663    16153326   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
```

Of course, I have more than one hard drive connected to it.  You should minimally have an "sda" drive listed.

---

### Post by Monotoko on 2011-06-09
> **polandee said:**
> That doesn't do anything. It doesn't cause an error, it just doesn't do anything.

Are you certain you put "sudo" at the start of the command? It won't output if not.

---

### Post by alphacrucis2 on 2011-06-09
> **polandee said:**
> That doesn't do anything. It doesn't cause an error, it just doesn't do anything.

That would suggest that the disk isn't being recognised. Reboot and see if the disk is seen by the system BIOS. The BIOS should display a message on bootup to tell you how to get into the config menu. Often F1 but depends on the particular BIOS. 

Make sure that the disk has power and is actually spinning up otherwise the BIOS won't be able to see it.

---

### Post by wep940 on 2011-06-09
Please also tell us more about the computer - brand, model, cpu, memory, the hard disk, etc..

This wouldn't happen to be an older PC that you've installed a driver larger than 132gb would it?

If this is an older PC with (P)ATA disk controllers only and you installed a SATA drive as the new drive but had to use an adapter to get the interface to (P)ATA, you should also be aware that a lot of the older PCs won't boot with a PATA to SATA adapter on the boot disk.

---

