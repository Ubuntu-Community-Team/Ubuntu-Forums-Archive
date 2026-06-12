---
title: "QPARTED partition question"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-03-24
1. I am working with a 500gig SATA drive. Its destinatio will be as drive 2 in a Lenove/IBM T61. However I have several other (desktop) machines used for work and testing. 

2. Started out with one normal partition (ntfs) containing only data. Put the drive in a desktop and using QPARTED live cd shrank the partition and placed it at the end of the drive, All was well. Could read and write to it.

3. Using QPARTED I copied a DOS partition to the beginning of the drive.

4. Using Qparted I then copued a good Ubuntu partition to the remaining free space.

5 Now have 3 partitions however they are recognized by QPARTED while in the desktop attached to port 0 of a sata card as:

Partition1 /dev/sda2
Partition2 /dev/sda3
Partition3 /dev/sda1

6. Installed in the T61 laptop as the second drive they are recognized in the same order but as /dev/hdx as opposed to /dev/sdx

7. Partition1 containing Freedos will boot.

The questions:

1. Why HDX instead of SDX from the same SATA drive?
2. Is the SDX or HDX order normally stated in the order in which the partitions are created?
3. Will this be a problem for multibooting or shoulf I recreate the drive to a 'normal' partition sequence?

All this just when I thought I had GRUB4DOS down pat in my mind!

---

### Post by carml on 2009-03-24
1. Are you sure the hard drive are of the same type?If it's so it looks strange to me.
2. As far as I know yes,they are.
3. I don't know a bit about,sorry. :(

---

### Post by mikechant on 2009-03-24
> 6. Installed in the T61 laptop as the second drive they are recognized in the same order but as /dev/hdx as opposed to /dev/sdx

> 1. Why HDX instead of SDX from the same SATA drive?


Is the T61 laptop running an older version of Linux? Going back a few years, IDE drives (SATA or PATA) used to show up as hdx and SCSI drives as sdx. Then the Linux kernel changed and all of these drives started showing up as sdx. I remember having to change my fstab entries from hdx to sdx, either when I upgraded to Fedora 4 or 6.

---

### Post by egalvan on 2009-03-24
> **mikechant said:**
> Is the T61 laptop running an older version of Linux?  IDE drives (SATA or PATA) used to show up as hdx and SCSI drives as sdx. Then the **Linux kernel changed** and all of these drives started showing up as sdx. I remember having to change my fstab entries from hdx to sdx, either when I upgraded to Fedora 4 or 6.

Not only the kernel, but some of the utilites also.

Parition utilities in particular...
older ones used hdx, newer ones use sdx.
GRUB also...

It's all the same, as that info is NOT on the drive itself,
rather in how each piece of software names the drives...

What DOES count is the ORDER in which each piece of software see the drives....

BIOS
GRUB
Linux kernel

each can see them in different orders, depending on how the info is passed on...

---

### Post by Al Fischer on 2009-03-24
> **mikechant said:**
> Is the T61 laptop running an older version of Linux? Going back a few years, IDE drives (SATA or PATA) used to show up as hdx and SCSI drives as sdx. Then the Linux kernel changed and all of these drives started showing up as sdx. I remember having to change my fstab entries from hdx to sdx, either when I upgraded to Fedora 4 or 6.

I don't think it would have anything to do with version of any software. The order in which they are shown is after using GPARTED live CD to copy partitions from several drives to one drive. The order and SDX or HDX terminology in the destination drive is what I am questioning. I was under the impression that the partitions on a drive were identified by the order in which they exist on the drive. Possibly this is not true and the SDX or HDX nomenclature comes from the source. But why would the SAME drive show up differently in the desktop  (as SDX) attached to port 0 of a SATA card or plugged into the removeable drive tray of a T61 laptop (as HDX)?

---

### Post by Al Fischer on 2009-03-25
bump

---

### Post by egalvan on 2009-03-27
> **Al Fischer said:**
> **I don't think it would have anything to do with version of any software.** The order in which they are shown is after using GPARTED live CD to copy partitions from several drives to one drive. The order and SDX or HDX terminology in the destination drive is what I am questioning. I was under the impression that the partitions on a drive were identified by the order in which they exist on the drive. Possibly this is not true and the SDX or HDX nomenclature comes from the source.** But why would the SAME drive show up differently in the desktop  (as SDX) attached to port 0 of a SATA card or plugged into the removeable drive tray of a T61 laptop (**as HDX)?

Yes, the nomenclature is directly related to the version of the software being used to access the drives...

Older versions of the kernel, and utilities (such as GRUB, parted, etc) used the hdx-style of naming...
newer versions use the sdx-style of naming...
some still have not up-dated to the new style, and remain with the hdx style.

The order in which they are seen by the software is determined by the order they are seen by the BIOS.
 This information is handed off to the software, which then uses it's own rules about numbering and naming.

partitions do NOT have to be in disk-drive order...
(I set mine up so they ARE in order, but that is just me,
I like the drives and partitions created in a certain order...
The BOOT drive will ALWAYS have four partitions, I ALWAYS create three primary and one extended.
If a drive will only have one partition (a data drive) it will be an EXTENDED partition.
I also use LABEL instead of UUID for my drives and partitions.
Again, **this is just my own personal prejudice showing**.)

As for why the SAME drive is showing up as different names,
the different types of hardware used to access the drive has an impact on the order is which it is seen, and exactly what piece of software does the access determines the name it is given...
again, some use hdx for IDE and sdx for SCSI(a disappearing standard)
and some use sdx for everything (the newer standard)
and some software starts counting with 0 (first is #0)
and some starts counting with 1 (first is #1)
of course all use 'a' as the first letter...

Which is one reason UUID became the default way to identify partitions...
UUID's belong to one, AND ONE ONLY, partition, are assigned at creation time,
and if the partition is erased, it's UUID is gone forever.
That is the theory... but I believe that the utility allows UUID's to be assigned, thereby rendering the **Universally Unique** part of the spec rather less valuable.
(same thing happened to MAC's... they were supposed to be Universally Unique also... tied to one, and one only, physical piece of hardware, never to be repeated...to uniquely identify it.)

and yes, this is problematic at times, and confusing... :)

---

### Post by Al Fischer on 2009-03-27
Your response got me far enough to get pointed in the right direction. Just spent 2 hrs and what I learned says I need to learn even more (typical)! Looks like the UUID is created when the partition is created and inasmuch as I copied the original partition the UUID was carried over from the PATA drive to the SATA drive and probably the SATA card now indetified it as what it wanted. It created the 'headache' described below from the link shown. Excellent reading. Additional problem was caused by my multiboot choice of GRUB4DOS as it appears to not handle a UUID in the ROOT term in the menu.lst. It wants the HDX or SDX. 

Looks like GRUB4DOS needs to be made able to use the UUID as all I read leads me to the conclusion that is the 'Chosen Standard' in Linux. And one nice thing about standards is that there are so many!

Thanks again for pointing me in the needed direction. I am never happy until I understand how it works. Then how to DO it is usually easy.  Linux is proving to be a real educational adventure. (and going well I might add)


[http://linuxshellaccount.blogspot.com/2008/08/how-to-manage-your-disk-by-uuid-on.html](http://linuxshellaccount.blogspot.com/2008/08/how-to-manage-your-disk-by-uuid-on.html)

snipped from the above link.

One, often unmentioned (but highly valuable), benefit of using UUID's to deal with your disks is that you don't have to worry about system naming conventions and the hassles inherent with using them. For instance, if you have a disk with a specific UUID and a block device name of /dev/sda3, if you do all your work (and system/application customization) with that disk, as the name /dev/sda3, you might be in for a big headache if you have a system problem (or just install some new hardware and reconfigure) and Linux decides to rename /dev/sda3 as /dev/sdb3 (or "anything" else). If you're using UUID's, you can simply use the "tune2fs" command (shown below) to assign the original UUID back to the new logical device name, so /dev/sdb3 would function exactly as if it were /dev/sda3, without causing any issues with your Linux OS :):

---

