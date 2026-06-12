---
title: "windows driver for ext partitions"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-22
I am trying to find a driver that will make my linux partition accessible in windows.  does any one know what i can use?  so far i have tried the following: diskinternals Linux Reader.  Disk internals just sits there scanning for my linux partition.

help

Trinidad

---

### Post by taurus on 2009-03-22
Didn't you already try fs-driver?  Can't access your ext3 with that?

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ronocdh on 2009-03-22
> **taurus said:**
> Didn't you already try fs-driver?  Can't access your ext3 with that?

[http://www.fs-driver.org/](http://www.fs-driver.org/)
I'll definitely vouch for this. I used it extensively years ago and never had a spot of trouble with it.

---

### Post by trinidadflores on 2009-03-22
> **ronocdh said:**
> I'll definitely vouch for this. I used it extensively years ago and never had a spot of trouble with it.That was the first one that I tried I could think of the name if it.  That worked fine by showing the drive; but when i would go to view the drive it would say "this drive needs to be formated in order to use it.  Would you like to format it now?"

---

### Post by LiamWilson on 2009-03-22
Don't you need to format your hd to use that?

---

### Post by trinidadflores on 2009-03-22
> **LiamWilson said:**
> Don't you need to format your hd to use that?

I understand that but that is what fs-driver tells me when i try and access my ubuntu partition.

---

### Post by trinidadflores on 2009-03-22
does any one have ideas of other ways i can access my linux partition in windows for my files?

---

### Post by 73ckn797 on 2009-03-22
> **trinidadflores said:**
> does any one have ideas of other ways i can access my linux partition in windows for my files?


The FS driver, I have experienced, only reads ext2. I cannot get it to read the ext3 format. That implies only one solution, reformat to ext2 and reload Ubuntu.

---

### Post by trinidadflores on 2009-03-22
which format is more secure the ext2 or ext3?

---

### Post by tabibito on 2009-03-22
I've been using FS driver for quite some time to read my ext3 partition on Windows. Been using it since Ubuntu Hardy.

It's been doing good until two months ago, when it suddenly told me that the disk needs to be reformatted when I tried to access it from Windows using the FS Driver. Anyone got a hint on this?

---

### Post by SunnyRabbiera on 2009-03-22
> **trinidadflores said:**
> which format is more secure the ext2 or ext3?

Both are on par with eachother for the most part in terms of security, the version numbers mean nothing for security.
But EXT3 does have more versatility...

[http://en.wikipedia.org/wiki/Extended_file_system](http://en.wikipedia.org/wiki/Extended_file_system)
[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by LiamWilson on 2009-03-23
Surely there must be a better or more updated version of this driver?

---

### Post by SunnyRabbiera on 2009-03-23
It doesnt seem so, for me FS driver works on machines I dual booted XP and linux on rather it be ext2 or 3

---

### Post by GepettoBR on 2009-03-23
I use FS Driver with ext3 since Gutsy, with no problems. Windows XP can access my disks perfectly - though since FS Driver doesn't support journaling, XP treats the ext3 partitions as ext2. You don't have to reformat, though. If you're getting that warning then something is wrong.

---

### Post by egalvan on 2009-03-23
> **GepettoBR said:**
> I use FS Driver with ext3 since Gutsy, with no problems. Windows XP can access my disks perfectly - though since FS Driver doesn't support journaling, XP treats the ext3 partitions as ext2. You don't have to reformat, though. **If you're getting that warning then something is wrong**.

There is nothing "wrong" here, just that fs-driver is out-dated...
(maybe if more folks would "tip" the software authors they may up-date the driver?)

quoted from their website
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

[B] Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. [/B]

---

### Post by jakupl on 2009-03-23
> **trinidadflores said:**
> That was the first one that I tried I could think of the name if it.  That worked fine by showing the drive; but when i would go to view the drive it would say "this drive needs to be formated in order to use it.  Would you like to format it now?"

It does the same for me, but only occasionally. Have you tried restarting windows, maybe several times. This does it for me.

---

### Post by gladson1976 on 2009-03-27
hi all

i've been having the same problem and i've found a driver that works with ext3 with 256 byte inodes. 

try the Ext2Fsd driver at 
[http://ext2fsd.sourceforge.net](http://ext2fsd.sourceforge.net)
it works with both read and write support.

---

