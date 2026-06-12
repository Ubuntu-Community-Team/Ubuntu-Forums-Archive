---
title: "FAT32 or NTFS for external hard drive?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by laptoplinux on 2010-02-28
I have a new hard drive, and it will be used with Linux, Mac, and Windows computers.  While I used to format them FAT32 a few years ago back when Linux's NTFS support was questionable, I hear that now ntfs-3g can easily and safely read and write on NTFS drives in both OSX and Linux.  I've looked this topic up on the web, but most of the posts are from 3-4 years ago and therefore not necessarily accurate anymore.

So, would it be a good idea to format the new drive to NTFS, or keep using FAT32?  Should I think about backing up the older drives and reformatting them to NTFS as well?  

One more question:  With the current NTFS support on Linux, if I delete a file, does it go into a "Trash" folder, or is it permanently deleted right then and there?  I seem to remember that it used to be the latter before.  Has that changed?  With FAT32, deleting the files moves them to the trash before permanently deleting them.

---

### Post by sandyd on 2010-02-28
> **laptoplinux said:**
> I have a new hard drive, and it will be used with Linux, Mac, and Windows computers.  While I used to format them FAT32 a few years ago back when Linux's NTFS support was questionable, I hear that now ntfs-3g can easily and safely read and write on NTFS drives in both OSX and Linux.  I've looked this topic up on the web, but most of the posts are from 3-4 years ago and therefore not necessarily accurate anymore.

So, would it be a good idea to format the new drive to NTFS, or keep using FAT32?  Should I think about backing up the older drives and reformatting them to NTFS as well?  

One more question:  With the current NTFS support on Linux, if I delete a file, does it go into a "Trash" folder, or is it permanently deleted right then and there?  I seem to remember that it used to be the latter before.  Has that changed?  With FAT32, deleting the files moves them to the trash before permanently deleting them.
1. I would go with NTFS, it has great support on LINUX, FAT32 is becoming a bit outdated anyways.
2. For me, their moved to the trash. but wether or not its moved to the trash is controled by the OS, not the filesystem.

---

### Post by theozzlives on 2010-02-28
NTFS supports larger file sizes, besides I think Windows abandoned FAT32 with Windows 7.

---

### Post by walt.smith1960 on 2010-02-28
> **theozzlives said:**
> NTFS supports larger file sizes, besides I think Windows abandoned FAT32 with Windows 7.

I hope not!  Most USB flash drives use FAT32. Or does Win7 have some sort of workaround? The file size issue can be a problem, especially with DVD ISO's.  I may install Win7......maybe......someday.....or not;).

---

### Post by Paddy Landau on 2010-02-28
NTFS is also a lot more efficient than FAT32.

---

