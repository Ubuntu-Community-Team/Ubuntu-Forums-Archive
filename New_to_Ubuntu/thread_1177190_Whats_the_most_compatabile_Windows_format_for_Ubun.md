---
title: "Whats the most compatabile Windows format for Ubuntu?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-06-03
Alright, i'm about to transition to Jaunty tonight. I want to make **~/Music**, **~/Videos**, and **~/Pictures** on a separate 500Gb disk, accessible from XP and ubuntu.

Ext3 is out because XP can't read it. should i go with FAT32 or are all the bugs worked out of NTFS in ubuntu?

.:EDIT:. I'm also open for different formats, all i care about is it works in both OS'es and is fast

---

### Post by nandemonai on 2009-06-03
I have that kinda stuff symlinked from home to a separate NTFS drive. No issues here. Pretty sure the issues with NTFS writes was ironed out a while back.

---

### Post by Dan_Dranath999 on 2009-06-03
yeah, i used to have an NTFS partition with movies, documents, music etc... so i could get my files from both linux & Windows.

Eventually, i got rid of that partition, and i probably will reformat the windows partition too, so i can use XP only on virtualbox.

---

### Post by ad_267 on 2009-06-03
NTFS is the way to go, it's a much better file system than FAT and I haven't had any problems with it or heard of anyone having any.

---

### Post by sica07 on 2009-06-03
NTFS is definitively the best alternative. FAT32 is deprecated.

---

### Post by cjv8888 on 2009-06-03
You can also install ext2 driver for Windows from [here.]("http://www.fs-driver.org/")
I think it can read ext3 also.

---

### Post by gn2 on 2009-06-03
> **cjv8888 said:**
> You can also install ext2 driver for Windows from [here.]("http://www.fs-driver.org/")
**I think it can read ext3 also.**

It certainly can.

---

### Post by binbash on 2009-06-03
go for NTFS

---

### Post by eMJayy on 2009-06-03
> **Sonic Reducer said:**
> Alright, i'm about to transition to Jaunty tonight. I want to make **~/Music**, **~/Videos**, and **~/Pictures** on a separate 500Gb disk, accessible from XP and ubuntu.

Ext3 is out because XP can't read it. should i go with FAT32 or are all the bugs worked out of NTFS in ubuntu?

.:EDIT:. I'm also open for different formats, all i care about is it works in both OS'es and is fast

My PC has 3 hard drives installed - a main system drive with Ubuntu and Windows 7 installed in dual boot configuration (I had XP installed up to a month ago) and two secondary drives formatted in NTFS. I use one of the secondary drives just to store music files, and the other is used to store pictures, videos etc. I started using Ubuntu last April and have not had a single issue with accessing, reading or writing to these NTFS drives. In fact, the data access speed has noticeably improved with Jaunty - it's to the point where I'm not noticing any difference between reading and writing speeds between Windows and Ubuntu. NTFS is definitely the way to go.

---

### Post by smartidiot on 2009-06-03
Avoid NTFS and FAT32.  As someone else previously stated, just use the Windows Ext2 and Ext3 driver from [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by egalvan on 2009-06-03
> **smartidiot said:**
> Avoid NTFS and FAT32.  As someone else previously stated,
 just use the Windows Ext2 and Ext3 driver from  [COLOR="Red"] [http://www.fs-driver.org/ ](http://www.fs-driver.org/ )[/COLOR].


Except that** Ext2 IFS version 1.11a** STILL DOES NOT SUPPORT large inodes, 
and Ubuntu uses large inodes by default.

Quote from the FAQ:

[COLOR="Red"]    * Inodes that are larger than 128 bytes are not supported.[/COLOR]

further quote:
[COLOR="Red"]
 Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes.
 Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again.
 Give the mkfs.ext3 tool the -I 128 switch.
 Finally, restore all files with the backup.
[/COLOR]

---

### Post by cjv8888 on 2009-06-04
> **egalvan said:**
> Except that** Ext2 IFS version 1.11a** STILL DOES NOT SUPPORT large inodes, 
and Ubuntu uses large inodes by default.

Quote from the FAQ:

[COLOR="Red"]    * Inodes that are larger than 128 bytes are not supported.[/COLOR]

further quote:
[COLOR="Red"]
 Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes.
 Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again.
 Give the mkfs.ext3 tool the -I 128 switch.
 Finally, restore all files with the backup.
[/COLOR]

Very interesting.
I once used Ubuntu's gparted to partition a drive and installed Puppy on it and Puppy was unable to find the Grub files until the inodes are converted back to 128.
Does anyone know from which Ubuntu release when the inodes become 256 bytes?

---

