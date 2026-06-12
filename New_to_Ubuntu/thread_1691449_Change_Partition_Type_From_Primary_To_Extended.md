---
title: "Change Partition Type From Primary To Extended"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by FooManChuBar on 2011-02-19
I have a new HP computer that I want to dual boot.  HP did not provide a Windows 7 CD.  There are already 4 Primary partitions set up and 4 is the maximum.  How can I change the partition type for one of the restore partitions to Extended?

---

### Post by Bucky Ball on 2011-02-19
Not really possible. An extended partition is basically a container for logical partitions (and you can have lots of them inside). You would need to delete one of the primary partitions then create an extended partition with the free space *then *create your logical partitions inside that.

I had a HP and you can make the recovery disks from the recovery partitions (instructions should be there in the windows install) then wipe the recovery and any other partitions you don't want/need. I made the recovery CDs then wiped the lot, installed Windows from the CDs I'd just made then Ubuntu.

---

### Post by FooManChuBar on 2011-02-19
> **Bucky Ball said:**
> Not really possible. An extended partition is basically a container for logical partitions (and you can have lots of them inside). You would need to delete one of the primary partitions then create an extended partition with the free space *then *create your logical partitions inside that.

I had a HP and you can make the recovery disks from the recovery partitions (instructions should be there in the windows install) then wipe the recovery and any other partitions you don't want/need. I made the recovery CDs then wiped the lot, installed Windows from the CDs I'd just made then Ubuntu.


Thanks man.  I thought that might be the case.

---

### Post by frotzed on 2011-02-19
Related: I've noticed a _lot_ of HP computers coming with four partitions out of the box.  I have yet to understand the logic for this.  I'm sure HP has their reasons, but I can't see how they're _good_ reasons.

---

### Post by srs5694 on 2011-02-20
It *is* possible, in some cases, to change a primary partition into a logical partition; however, this requires at least one free (unallocated) sector immediately prior to the partition that's to be so converted. I know of no Linux utility that's designed to make this change, although it's possible to do it with sfdisk or gdisk. IIRC, the Windows [Partition Wizard](http://www.partitionwizard.com/) program includes an option to do this, although I've never tried it.

One of the four partitions that HP provides serves as an emergency recovery system; it is essentially provided in lieu of a physical DVD with a copy of Windows. If Windows becomes so badly corrupted that it won't boot and can't be repaired, you can recover the system to its from-the-factory state using the recovery partition.

In your situation, FooManChuBar, I recommend you do the following:


[list=1]
[*]Locate the utility in Windows that enables you to create a set of emergency recovery DVDs. Run this program twice (making to sets of DVDs). While running this program, write a letter to HP (with a cc: to Microsoft) telling them you think they're cheap and inconsiderate to not include a Windows DVD with the computer.
[*]Using the Windows partition management tool, delete the recovery partition (partition #3, IIRC), which is normally something like 15 or 20 GiB in size.
[*]Using the Windows partition management tool, resize and/or move the other partition(s) so that you've got however much free space you want for Linux and for any data exchange partition(s) you might want.
[*]Reboot into the Ubuntu installer and select the manual partitioning option.
[*]Create an extended partition and, within it, as many logical partitions as you want for Linux, its swap space, and Linux/Windows shared-data partitions.
[*]Proceed with Linux installation.
[/list]

---

### Post by Bucky Ball on 2011-02-20
Don't worry, Toshiba does something equally as ludicrous. Why they just can't provide a recovery CD/DVD is beyond me.

---

