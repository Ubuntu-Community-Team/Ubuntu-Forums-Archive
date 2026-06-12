---
title: "GRUB loading, please wait... Error 18"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by alecw on 2009-06-20
Hi there

Completely new and ignorant with all of this - tho very willing to learn

Downloaded Ubuntu to  my old PC
Made the disc
Completed the install
Rebooted and immediately after the screen wher you have the option to enter Bios I get the following:

Verifying DMI Pool Data...........Update Sucess
Boot from CD :
GRUB Loading stage1.5

GRUB loading, please wait...
Error 18

I have attempted a dual boot

Have no idea what to do, or how to return to windows or wipe everything and start again

Any help great fully received

Alec

---

### Post by halitech on 2009-06-20
How big is the hard drive and how old is the computer?

According to here: [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

it's an issue with linux partitions being beyond the end of the LBA

>   Error 18 on Dual Boot Systems Using a Single Hard Drive

This error often occurs when creating a dual boot system (with Windows) on a single hard disk drive, as in a notebook PC, because the Linux partitions end up being beyond the LBA range. On a large notebook drive you may need to re-install Windows into a smaller primary partition (or resize the partition), then create an extended partition in the unallocated space and create partitions for Linux Root, Linux Swap, and Linux Home, then in the remaining unallocated space create another NTFS partition for Windows. In other words, the Linux partitions must be immediately after the Primary Windows partition so they are still within the LBA range, then you can place additional NTFS or FAT32 partitions after the Linux partitions.

On a 160GB notebook drive, the following gave Error 18:

Primary: 80GB Windows NTFS

Extended: 4GB (FAT32), 50GB (NTFS), 4GB Linux Root (ext3), 2GB Linux Swap, 20GB Linux home (ext3).


The following worked:

Primary: 80GB Windows NTFS

Extended: 4GB Linux Root (ext3), 2GB Linux Swap, 20GB Linux home (ext3), 4GB (FAT32), 50GB (NTFS).

It can be somewhat of an annoyance to have the NTFS file system split into two partitions, but it's a workaround.


[Note: the reason for the 4GB FAT 32 partition is that it makes it possible for both Windows and Linux to access that partition, which can be useful when transferring files between the two operating systems.]
Removing GRUB After Error 18 on a Dual Boot System (Windows/Linux) Using a Single Hard Drive

If you install GRUB on a dual boot system with a single hard drive, and get Error 18, you will not be able to boot Windows. To fix this, you need to boot the system from a Windows Recovery CD, select "R" for Repair, and then run "fixmbr" (fix master boot record) at the DOS prompt in C:\windows. This will remove GRUB. If you don't have a recovery CD, you can download floppies from Microsoft for XP, see "http://support.microsoft.com/kb/310994".

[http://wiki.linuxquestions.org/wiki/GRUB#ixzz0IytrBILz&D](http://wiki.linuxquestions.org/wiki/GRUB#ixzz0IytrBILz&D)

---

### Post by alecw on 2009-06-20
Thank you
Looks scary - nothing ventured nothing gained!

---

### Post by halitech on 2009-06-20
only as scary as you let yourself think it is :)

---

### Post by alecw on 2009-06-20
right daft question
really don't know what I am doing
more than happy to loose windows all together :)
if I load again and don't attempt a dual boot - sounded complicated any way
do you think it will run?
Does mean i think I will then have 3 versions of Ubunto loaded
Am i barking up the right tree
sorry for being ditsy
born that way!

---

### Post by halitech on 2009-06-20
it shouldn't give you 3 versions. when you get to the partitioning stage, just tell it to use the entire disk if you want to wipe out windows completely. Do you have another system you can use to get online in case something happens and doesn't work?

---

### Post by alecw on 2009-06-20
yip
on my little acer one right now
it's what got me started on the whole linux thing
it's a dream :-)
especially for the easily frustrated like me!
looks like it's going swimmingly
I'll let you know if i get in this time
thank u so much x

---

### Post by halitech on 2009-06-20
well good luck and I'll keep my fingers crossed for you this time around :)

---

### Post by alecw on 2009-06-20
Yee - ha!
I reckon we've done it

Thanks for your patience

Have to dash before I can play with it :-(
Fridge empty - need wine!

My thanks again

Alec x

---

### Post by LewRockwell on 2009-06-20
then there is always [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

