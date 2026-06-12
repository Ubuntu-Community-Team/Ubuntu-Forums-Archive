---
title: "Problem Mounting Truecrypt"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by getitright on 2009-08-06
I have had Truecrypt working well for some time, but somewhere along the line I must have altered something as when I try to mount now the message

"mount: you must specify the filesystem type"

is displayed.

---

### Post by Ubun2 Us3r on 2009-08-06
just an idea, but when you made the volume, did you forget to list what format you wanted it in? e.g. FAT32, NTFS, ext3, etc.

---

### Post by getitright on 2009-08-06
> **Ubun2 Us3r said:**
> just an idea, but when you made the volume, did you forget to list what format you wanted it in? e.g. FAT32, NTFS, ext3, etc.

The volume has been working OK until yesterday and I have not altered the file system. The volume was set up some months ago and I cannot remember the file system selected.

---

### Post by niteshifter on 2009-08-06
Hi,

What version of truecrypt are you using?

---

### Post by getitright on 2009-08-06
> **niteshifter said:**
> Hi,

What version of truecrypt are you using?

Truecrypt 6.2a.

I have solved my immediate problem in that I had a back up Truecrypt volume which I was able to copy across and this worked as it should. However I would still like to know, for future reference how to resolve my original problem as I may not have a backup copy of the volume next time.

Incidentally the only file system options for Truecrypt are FAT32. Ext2 and Ext3, is it possible to set the volume up as NTFS.

---

### Post by niteshifter on 2009-08-06
> **getitright said:**
> Truecrypt 6.2a.

I have solved my immediate problem in that I had a back up Truecrypt volume **which I was able to copy across and this worked as it should**.

That suggests it wasn't anything you did to TC, rather that the volume had become corrupted.

Backups are your best defense against such things ;) Another defensive measure is to run fsck on the volume occasionally - TC volumes are not immune to corruption and the system fsck doesn't reach the file system contained in one. Starting with version 6.x TC makes it easy to check and repair a volume's file system: Open as you would normally, right-click on it in the GUI's volume list - select check or repair as you please.

As to creating a NTFS file system: I don't know. I suspect you can but I don't use NTFS much.

---

### Post by Ubun2 Us3r on 2009-08-06
as for NTFS, yes you can in Truecrypt 6.2a. There should be an option when creating the volume that asks whether you will just use it on linux or on windows as well. If you tick windows as well, it gives NTFS as an option

---

