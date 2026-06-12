---
title: "How Ubuntu sees the Hard Disk ?"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by sathee on 2011-03-10
Hi All,
 
I am very new to Linux.
I have installed Ubuntu in my laptop yesterday.
While installing Ubuntu i could able to see the message,
installing ext4 journaling file system in scsi1(0,0,0)
 
I have got SATA disk in my laptop.
But Ubuntu is seeing it as SCSI disk.
Since i am storage professional, i have lot of interest in
how Ubuntu visualizes the hard disk ?
Could anybody explain me ?
 
 
Advance Thanks.
 
- Sathees:p

---

### Post by Hedgehog1 on 2011-03-11
sathee,

To Unix & Linux, all hard drives are seen as SCSI, even if they are really IDE or SATA or a Raid Array or (on rare occasion) SCSI.

The **S**mall **C**omputer **S**ystems **I**nterface (SCSI) was just a practical standard to work with and code low level routines against.

In reality, the OS is hard drive interface agnostic, and this allows greater freedom in hardware configurations.

***The Hedge***

:KS

---

### Post by sathee on 2011-03-11
Hi,
 
Thanks.
 
But again, to perform any type of action up on disks, will 
Ubuntu( Linux/UNIX) use, SCSI protocol ?
 
Is it a Emulation ?
Thanks :D
 
-sathee

---

### Post by mcduck on 2011-03-11
Couple of years ago Linux developers noticed that their SATA/SCSI driver actually handles all discs better than the old PATA driver did, so now all discs use the same driver regardless of what interface they are connected to.

(Although even before that SATA and SCSI discs were using the same driver, and it was just PATA drives that were using a driver of their own).

So no, it's not emulation. It's just that it doesn't matter what the interface you use is, the driver is still the same and handling all drives the same way regardless of the interface is simpler since there's no real reason to threat the drives differently.

---

### Post by fabricator4 on 2011-03-11
> **sathee said:**
> 

But again, to perform any type of action up on disks, will 
Ubuntu( Linux/UNIX) use, SCSI protocol ?

Yes, the layered architecture of Linux lends itself to this.  The simple nature of the SCSI interface has defined the IO layer and how block devices are used.  There's a lot of history. The end result is the ability to use almost any device with the implementation of a simple low level block device driver.

I recall installing SCO unix (many years ago) and SCSI drives were the norm.  If you wanted to use other drives (MFM and RLL at the time) it required installing block device drivers.  Getting a UNIX box booting off (for example) an MFM drive was non-trivial and not for faint hearted.  I wouldn't have know where to start. 
 
> 
Is it a Emulation ?


Well, not exactly, no. The block device drivers all work with the buffers and cache in the same way, regardless of what the device is.  This isn't an "emulation" but a practical and efficient method of standardising IO.

Historically the architecture didn't come out of the requirements of SCSI alone, it's simply good design that allowed a lot of flexibility that proved itself to be future proof. The history has however left us with a hangup about the terminology with use: sda still means "SCSI device a", same as it did in 1987.

A quick Google search came up with [this]("http://www.ibm.com/developerworks/linux/library/l-scsi-subsystem/") which seems like a reasonably useful introduction to the subject.

Chris.

---

### Post by psusi on 2011-03-11
Yes, it is emulation.  The middle layers of the kernel IO stack speak the SCSI command set.  These days the ATA command set is pretty similar, so libata trivially translates between the two.

---

