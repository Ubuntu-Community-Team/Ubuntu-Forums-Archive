---
title: "What (if any) Filesystems (EXT2/3/4) can windows read/write..."
date: 2010-02-23
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-02-23
... As the title says, what filesystems can windows read/write to without too much hassle and tweaking/downloading.

---

### Post by atomizer on 2010-02-23
FAT and NTFS. I have tried reading ext3/4 in Windows with 3rd party software, with no succes.

---

### Post by JamesParnell on 2010-02-23
Problem with that is I want to work between both Ubuntu and Windows, Ubuntu on my external, and windows as my primary. 

Now, when installing Ubuntu on the external, you cant install as NTFS....and FAT isnt great. Unless it's better for Ubuntu than windows (FAT32 I mean)

---

### Post by Bachstelze on 2010-02-23
> **JamesParnell said:**
> Problem with that is I want to work between both Ubuntu and Windows, Ubuntu on my external, and windows as my primary. 

Now, when installing Ubuntu on the external, you cant install as NTFS....and FAT isnt great. Unless it's better for Ubuntu than windows (FAT32 I mean)

Why not create a FAT or NTFS storage partition on your external drive, and store your data there? You probably don't need to access your Ubuntu system partitions from Windows.

---

### Post by atomizer on 2010-02-23
Maybe you can make a seperate data- partition, formatted in FAT32 or NTFS? I wouldn't put the linux system on an FAT or NTFS partition, because of the rights managment of files

---

### Post by JamesParnell on 2010-02-23
> You probably don't need to access your Ubuntu system partitions from Windows.
Up until yesterday I would of agreed with you, except that yesterday, my Windows system failed and the recovery disc was too scratched to repair it. Luckily for me, my netbook was trashed so I ripped out my HDD (which is now in an enclosure and being a secondary HDD) and booted into Ubuntu, Saving everything I needed to save before formatting. Then, guess what, my Ubuntu system needed to be wiped clean as it had been messed up from moving from a netbook to desktop system. So now I'm at the stage where I'm running the LiveUSB on my desktop machine, figuring out which filesystem to use so that if I need to get to one of the systems, be it Ubuntu or Windows, I can do without having to loose everything (again).

---

### Post by The Cog on 2010-02-23
Windows might be able to read/write ext2 with the aid of a downloaded driver. But I gather that it can't read recent versions of ext3, and can't read ext4, xfs, jfs, reiserfs etc. Pretty-much, windows can't read linux partitions. So you will either need to rely on live CDs or better still, on using backups that you took earlier.

---

### Post by switch10 on 2010-02-23
check out Ext2IFS. It says it works with windows 7 and can read and write ext2 and ext3.  I haven't tried it yet.

---

### Post by oldfred on 2010-02-23
I have and recommend a shared NTFS partition for any data you may want to share between systems. In most cases it is better not to use third party tools to directly write into the operating system partition. Some windows users recommend a separate data partition even if you just have windows so when windows dies you still have your data.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Shared linux data partitions:
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

