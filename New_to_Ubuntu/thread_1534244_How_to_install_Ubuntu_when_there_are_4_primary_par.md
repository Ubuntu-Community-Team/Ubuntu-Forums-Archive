---
title: "How to install Ubuntu when there are 4 primary partitions already"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by cjv8888 on 2010-07-19
Just bought a Compaq notebook which has Win 7 pre-installed and occupying 4 primary partitions on the disk. 

1. A boot partition
2. Win 7 
3. Recovery partition
4. HP tools.

I want to install Ubuntu but am reluctant to remove any of the above as the thing does not even come with a recovery disc.

Any suggestion as to how I can make room to install Ubuntu?

Is there any way to convert one of those primary into an extended?
or just have to use wubi?

---

### Post by mikewhatever on 2010-07-19
If all 4 are primary partitions, and you can't/don't want to remove one of them, you'll need another hdd.

---

### Post by theozzlives on 2010-07-19
I'm thinking you can backup one of those, create your extended and 2 logical partitions (Ubuntu can boot from a logical drive), and restore your data. You can make a backup of one of the partitions by booting the live CD and make a  tarball of the data, it's pretty easy. I'd prolly say the hptools.

---

### Post by Paqman on 2010-07-19
> **cjv8888 said:**
> 
or just have to use wubi?

That would certainly be the easiest solution. Longer term you could look at getting another drive and migrating your Wubi system onto it.

I'd do some homework and find out what the HP Tools partition is though. It's possible you could image it then restore it inside an extended partition. If it didn't work you could always resotre the image back to a primary partition. No harm, no foul.

---

### Post by cjv8888 on 2010-07-19
The recovery partition is a ntfs partition but you cannot look inside it, whether from Windows or on the live CD.

The HP tools partition is a FAT32 which contains some system Diags files.

In the event of a recovery, is it dependent on these tools or is it done entirely from the recovery partition?

---

### Post by plucky on 2010-07-19
> **cjv8888 said:**
> The recovery partition is a ntfs partition but you cannot look inside it, whether from Windows or on the live CD.

The HP tools partition is a FAT32 which contains some system Diags files.

In the event of a recovery, is it dependent on these tools or is it done entirely from the recovery partition?

@cjv8888

What is you recovery strategy if you should have a hard drive crash?

You should always have a copy of your recovery partition on DVD and I believe that HP normally provides tools to create recovery DVDs.You should also copy the HP tools partition as well.

Check your user documentation as to how to backup the recovery partitions.

Good Luck

---

### Post by cjv8888 on 2010-07-20
I backed up the recovery partition on DVDs and also copied the HP tools onto another drive, then I deleted the HP tools partition, shrank the Win 7 partition and installed Lucid.  All went well.

My question now is:
The grub menu now shows 3 entries for Windows.
Windows 7 loader
Windows Vister loader
Windows Vister loader

The first one boots Win 7. The last one boots the recovery partition.  The middle one will not boot.

How do I change these entries?

I read through the grub 2 tutorial and could not find any way of editing these, only a way to add to them.

---

