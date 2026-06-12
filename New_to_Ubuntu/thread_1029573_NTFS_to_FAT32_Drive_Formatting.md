---
title: "NTFS to FAT32 Drive Formatting"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Bouldaire on 2009-01-03
I am trying to re-format a SimpleTech 160 GB external hard drive from its present state of NTFS to FAT32 so my Ubuntu Dell Laptop (Mini 9) will recognize (mount) the drive.  I have been unsuccessful on a WinXP machine and my Ubuntu laptop.  Any thoughts?  Is this even possible to do?  Thanks!  --Bouldaire

SOLVED

---

### Post by Gannon8 on 2009-01-03
How are you trying to format it? What are you doing to it?

Install GParted from the Add/Remove programs, and open up a terminal and execute:
```
gksudo gparted
```
Choose your USB Hard drive, right click on the partition and select format as FAT32. If it does not work, tell us if there are any errors on the screen or in the terminal.

---

### Post by bobnutfield on 2009-01-03
It is indeed possible, but not necessary as Ubuntu is perfectly capable of mounting an ntfs filesystem.  You will need to install ntfs-3g (which is aavailable in the repos0.  once installed, ntfs filesystems will mount and can be written to.

---

### Post by handydan918 on 2009-01-03
This should be trivial. You say you failed, but make no mention of what you tried. 
How about using gparted,making sure the external dirve is unmounted, and reformatting?

BTW, you should be ble to read/write ntfs, anyway.

```
sudo apt-get install ntfs-3g ntfsprogs
```should ensure that you have the right stuff installed...

---

### Post by Bouldaire on 2009-01-03
Bob, When I completed your suggestion I saw the main drive and the external in the gparted window.  The external drive has a "keys" icon which to me means it is locked out; therefore the "format to" is grayed out.  How do I unlock those keys?  Thanks, Bouldaire

---

### Post by Bouldaire on 2009-01-03
Gannon8, When I completed your suggestion I saw the main drive and the external in the gparted window. The external drive has a "keys" icon which to me means it is locked out; therefore the "format to" is grayed out. How do I unlock those keys? Thanks, Bouldaire

---

### Post by bobnutfield on 2009-01-03
> **Bouldaire said:**
> Bob, When I completed your suggestion I saw the main drive and the external in the gparted window.  The external drive has a "keys" icon which to me means it is locked out; therefore the "format to" is grayed out.  How do I unlock those keys?  Thanks, Bouldaire

The keys indicate that you are trying to format a mounted drive.  Make sure the drive is not mounted before trying to format it.

---

### Post by bump_ on 2009-01-03
Just a suggestion.

If your only reason for reformatting is to get Ubuntu to see the drive, it is unnecessary. If you download the ntfs-3g package, your laptop should be able to read ntfs drives.

---

### Post by HotShotDJ on 2009-01-03
FAT32 is a poor choice for a large drive.  It was designed to work with floppy drives (FAT16) and then extended to deal with the small (by today's standards) hard drives.  It is not suited to modern hard drives.

There are two options (perhaps more, but these are the simplest) to deal with using a USB hard drive with both Linux and Windows.  The first is to simply stick with NTFS.  As noted in an early post to this thread, you will need to use ntfs-3g -- which is installed by default in Ubuntu 8.10 (perhaps in some earlier versions as well, but definitely in 8.10).  You must also enable write support, since this is disabled by default.  This is EASILY accomplished by installing ntfs-config (System --> Administration --> Synaptic Package Manager).  Once installed, you can enable write support by running Applications --> System Tools --> NTFS Configuration Tool.

The second option is to use ext3 file system.  Of course, this is supported in Linux by default.  On you Windows system(s), you would need to install drivers. see: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) -- despite its name (EXT2 Installable File System for Windows), it will also work with ext3 file systems.

The first option is probably the easiest.  Using FAT32 on a 160 Gig drive is probably the worst choice.

---

### Post by Bouldaire on 2009-01-03
Bob,  I did that and then I was able to select FAT32.  The message I have now is "operation pending" which suggests that it is reformatting to the FAT32 filesystem.  Thanks very much.  Bouldaire

---

### Post by bobnutfield on 2009-01-03
> **Bouldaire said:**
> Bob,  I did that and then I was able to select FAT32.  The message I have now is "operation pending" which suggests that it is reformatting to the FAT32 filesystem.  Thanks very much.  Bouldaire

That's fine if that is what you really want to do, but as many others have posted, Ubuntu will read and write to ntfs disks just fine.  But, if you just truly want a fat32 files system on the disk, I guess you have succeeded.

---

### Post by dragos_iliescu_2005 on 2009-01-03
ntfs is better choice to fat32. do not reformat the drive. Ubuntu is able to mount ntfs drives.

---

### Post by Bouldaire on 2009-01-03
HotShotDJ,  I will take your advice as I have just gone back to the NTFS filesystem.  I am now able to access/read that external drive; no more error messages.  So thanks a million.  --Bouldaire

---

### Post by Bouldaire on 2009-01-03
Thanks!!

---

