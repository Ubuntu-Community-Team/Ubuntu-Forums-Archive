---
title: "new installation new hard drive - partition how?"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by endsuit on 2011-01-15
I have redone an older desktop computer with a new motherboard (MSI) with AMD processor, Asus video card (supposedly ready for Crossfire what ever that is) and 1 TB Segate hard drive.  I have downloaded at the office Ubuntu 10.10 to be (at least for now) the only Operating System.

From the CD drive i loaded on Ubuntu and then went to partition the hard drive.  I wanted to at least spit the 1 TB into two partitions, but kept coming up with a requirement for a root partition and in the previous menus there was no such option.

How do I put in the necessary partitions on the new drive?  The suggested sizes of the partitions seemed small. Are there any suggestions?
The rehab is at home and the computer I am on is at the office.  Should I pull the hard drive out and bring it down to the office stick it into my Windows XP computer to partition it?

Thanks.

---

### Post by plucky on 2011-01-16
> **endsuit said:**
> I have redone an older desktop computer with a new motherboard (MSI) with AMD processor, Asus video card (supposedly ready for Crossfire what ever that is) and 1 TB Segate hard drive.  I have downloaded at the office Ubuntu 10.10 to be (at least for now) the only Operating System.

From the CD drive i loaded on Ubuntu and then went to partition the hard drive.  I wanted to at least spit the 1 TB into two partitions, but kept coming up with a requirement for a root partition and in the previous menus there was no such option.

How do I put in the necessary partitions on the new drive?  The suggested sizes of the partitions seemed small. Are there any suggestions?
The rehab is at home and the computer I am on is at the office.  Should I pull the hard drive out and bring it down to the office stick it into my Windows XP computer to partition it?

Thanks.

From the Ubuntu CD assuming it is the desktop CD.

Open **System > Administration > Gparted** and use that to create whatever partitions you require.

I would recommend a 20Gb / (root) partition and the rest shared between a /home and /Storage partitions encased within an extended partition.

Good Luck

---

### Post by coffeecat on 2011-01-16
> **endsuit said:**
> Should I pull the hard drive out and bring it down to the office stick it into my Windows XP computer to partition it?

No. Windows cannot create the Linux filesystems necessary for Ubuntu. Gparted is the only partitioner you need.

You must have a root partition for the main Ubuntu filesystem. A swap partition is a good idea. If you don't want the root partition to sprawl all over 1TB, then a separate home partition and/or data partition is a good idea. A root partition can be as small as 10-15GB if you keep your data on a separate partition. I've never had an Ubuntu installation go much above 5GB - and that's with a lot of extra apps installed - with my personal files on another partition.

You might find this link useful. Read all the links in it:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

