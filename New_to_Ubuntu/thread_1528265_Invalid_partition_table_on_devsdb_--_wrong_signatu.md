---
title: "Invalid partition table on /dev/sdb -- wrong signature 0."
date: 2010-07-10
forum: New to Ubuntu
---

### Post by tmdpny on 2010-07-10
OK I'm not fully sure what I did.  I had two drives in my computer, one for the operating system and general use and another (a 1TB) for mass storage.

The main drive crashed.  I booted from a CD and tried to install Ubuntu to the mass storage drive until I got a replacement drive.  I had that drive partitioned, and during the install I offered one of my partitions to the software.  

I eventually bought a new replacement drive and installed Ubuntu on it.  I then went to restore my mass storage drive to the way I had it before.  I deleted the partition created when I put the OS on it, then went to recreate a new partition as it was originally.

Sadly, it isn't working.  I get the following error

Invalid partition table on /dev/sdb -- wrong signature 0.

The full error is:
```
Error creating partition: helper exited with exit code 1: In  part_add_partition: device_file=/dev/sdb, start=419423477760,  size=262147931136, type=0x83
Entering MS-DOS parser (offset=0,  size=1000204886016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 209711706624, type 0x07)
new  part entry
looking at part 1 (offset 209711770112, size 790492370432,  type 0x0f)
Entering MS-DOS extended parser (offset=209711770112,  size=790492370432)
readfrom = 209711770112
MSDOS_MAGIC found
readfrom = 681571376640
MSDOS_MAGIC  found
readfrom = 863276037120
No MSDOS_MAGIC found
Exiting  MS-DOS extended parser
looking at part 2 (offset 0, size 0, type  0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new  part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing  partition table scheme = 1
got it
Error: Invalid partition table  on /dev/sdb -- wrong signature 0.
ped_disk_new() failed


```I am at a complete loss.  I made sure that I am an administrator, I rebooted the system, I tried booting from a CD version, etc.  What am I missing as the problem?

---

