---
title: "Using files across Windows &amp; Karmic partitions"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-14
Can one hard disk drive with both Win 7 and Karmic installed share files or directories across the partiitons? 

If it is possible how do I set that up?

I've been netsearching these forums and Google for half and hour and am getting conflicting results and recommendations.

p.s., on this hard drive, win 7 was installed before karmic.

---

### Post by Mustard on 2010-02-14
A few things I know about this are that windows can't read the ext4 filesystem, whereas linux can read the NTFS filesystem.  Both systems can access FAT32 quite transparently.  Windows has software that allows you to read ext2 and ext3 filesystems.

Probably the easiest way is to have an 'extra' partition formatted in FAT32 or NTFS that would be an interchange point for files between the two operating systems.

..or you could access ext2/ext3 shared partition files (read only I think), from Windows using freely available windows compatible applications.

Karmic is using ext4 as its default.

---

### Post by night_fox on 2010-02-14
Karmic and win7 can indeed share files, but only if the filesystem can be read by both systems, so your best bet is to tell linux that your home directory is in your windows partition.

Linux can read all windows filesystems
Windows can't read all linux filesystems.

---

### Post by Mark_in_Hollywood on 2010-02-14
How can I get Karmic to read .html, .pdf. and .doc files from the Win 7 side of the partion?

I don't want to read/copy/move/edit .dll, .ini or any ms-filesystem stuff, only files such as one may see over the 'net.

---

### Post by Mark_in_Hollywood on 2010-02-14
[QUOTE=night_fox;8827285]Karmic and win7 can indeed share files, but only if the filesystem can be read by both systems, so your best bet is to tell linux that your home directory is in your windows partition.



How do I tell Karmic that that the / is in the windows partition?

---

