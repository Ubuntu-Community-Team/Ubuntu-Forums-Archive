---
title: "Considering a dual-boot machine..."
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Neostar2119 on 2011-07-06
Just a quick question...

I currently run a Windows 7 box that I'd like to consider dual-booting.

I understand there is a operation I can perform that will allow me to build separate partitions for the two operating systems, and a third partition that is shared between the systems for my personal files.

My question is, can I do this without having to destroy and reformat my Win7 partition?

or am I stuck having to start fresh?

Thanks for your insight guys.

---

### Post by Matt__ on 2011-07-06
You can either partition windows using windows admin tools/volume manager or let Ubuntu do it during install (there are either easy auto options or advanded).
I suggest you defrag your pc and back up your data before doing anything.

there is an illustrated install guide here; [http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

#edit: once youre installed there are several post install guides to finish things off; [http://www.my-guides.net/en/guides/linux/206-ubuntu-natty-narwhal-1104-post-installation-guide-](http://www.my-guides.net/en/guides/linux/206-ubuntu-natty-narwhal-1104-post-installation-guide-)

---

### Post by aeiah on 2011-07-06
it may be easier just to mount your windows partition in linux but the method you had in mind would be cleaner.

needless to say, whichever you do, back the important stuff up first. you'll find it easier if you back up your stuff to one big secondary drive, detach it, then remove the personal data from windows, shrink the windows partition (leaving some space for additional growth, obviously), and install ubuntu in the spare space. this'll remove the danger of accidentally wiping your data or ending up with a corrupted partition if something goes wrong. shrinking and moving partitions dont always go well.

if you were to just keep all your data on your windows partition, then in ubuntu you could map your music, documents, pictures and videos folders from your windows partition into your ubuntu home folder. the data would stay on your windows partition but be accessible, and convenient, whilst in ubuntu.

---

### Post by Jacobonbuntu on 2011-07-06
> **Neostar2119 said:**
> Just a quick question...

I currently run a Windows 7 box that I'd like to consider dual-booting.

I understand there is a operation I can perform that will allow me to build separate partitions for the two operating systems, and a third partition that is shared between the systems for my personal files.

My question is, can I do this without having to destroy and reformat my Win7 partition?

or am I stuck having to start fresh?

Thanks for your insight guys.


I would suggest to resize the Windows partition and create a shared partition (can be ntfs) by the Windows tools, leaving part of the disk unused. Then install Ubuntu in the free space. I had a bad experience once letting Linux resize a Windows (system-)partition.
Of course make backups before you do anything....

---

### Post by wildmanne39 on 2011-07-06
Hi, I have never had a problem resizing partitions in ubuntu, but the recommended way is to use windows to resize the partition, but you you do not format the ubuntu partition, you do that from ubuntu livecd, and it is recommended to run defrag on windows three times before shrinking the partition

---

### Post by darkomano on 2011-07-06
Check your partitions before starting - use Disk Management to view current partitions.
Usually Windows 7 install creates 2 partitions - one called "System reserved" some 100 MB where the boot files are stored and a second for Windows 7 itself.
These are two primary partitions.
You can have only 4 primary partitions in total or 3 primary + 1 extented.
The extented can have multiple logical partitions.
 
So in your case it is best to create the data partition as primary. 
Then create an extented partition which later will be used by Ubuntu install to create at least 2 partitions - the root and swap partitions.
 
Choose all partition sizes carefully as resizing later will lead to boot problems!
 
You can use either Ubuntu boot loader - GRUB2 - as base for the dual-booting or 
Windows 7 boot loader.
 
If you choose Windows 7 boot manager to control the dual-boot you can use the file boot.img from GRUB2 boot directory to chain-load Ubuntu. See here [http://boyans.my3gb.com/VBCD_How To.html](http://boyans.my3gb.com/VBCD_How To.html)
 
In either case have your Windows 7 install DVD or Win 7 Repair CD ready.
!!!Backup your user data!!! before any partition resizing, moving etc.

---

### Post by Mark Phelps on 2011-07-06
Since your PC came preloaded with Win7, you most likely do NOT have Win7 media; therefore, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy later if you need to repair the Win7 boot loader from problems during the dual-boot setup.

Also, do NOT use the Ubuntu installer to shrink the Win7 OS partition to make room for Ubuntu.  Win7 is very touchy and using Linux utilities on its OS partitions risks corrupting the filesystem and rendering it unbootable.  Use only the Win7 Disk Management utility to shrink the Win7 OS partition.

And, if you already have four partitions, do NOT allow the utility to create any more partitions.  If you do, it will change your partitions into Dynamic Disks -- and that will cause you major problems.

---

