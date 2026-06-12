---
title: "Can't Access 2nd Hard Drive Ubuntu 8.10"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by zutronius on 2009-02-02
I am unable to access my second hard drive. I am using two 250 sata drives in my machine and I have ran fdisk and this is what it comes up with.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db3bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29646   238131463+  83  Linux
/dev/sdb2           29647       30401     6064537+   5  Extended
/dev/sdb5           29647       30401     6064506   82  Linux swap / Solaris


I am unable to access the second hard drive however. What do I need to do to be able to access the second drive?

---

### Post by &#32 Greg on 2009-02-02
Is /dev/sda the unaccessable one? Because it looks like there's no partitions on it.

---

### Post by taurus on 2009-02-02
> **zutronius said:**
> I am unable to access my second hard drive. I am using two 250 sata drives in my machine and I have ran fdisk and this is what it comes up with.

[B]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000[/B]

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db3bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29646   238131463+  83  Linux
/dev/sdb2           29647       30401     6064537+   5  Extended
/dev/sdb5           29647       30401     6064506   82  Linux swap / Solaris

I am unable to access the second hard drive however. What do I need to do to be able to access the second drive?

I guess your "second" harddrive is /dev/sda and currently, there is no partition or filesystem on it.  Perhaps you need to use gparted in System -> Administration (install it if you don't have it on your machine) to create a partition, /dev/sda1, and format it to ext3 or whatever filesystem you want.  Then, you can mount it by adding an entry in /etc/fstab.

---

### Post by zutronius on 2009-02-02
Thanks! I'm just upgrading ubuntu then I will try what you said to do! Many thanks!!

---

