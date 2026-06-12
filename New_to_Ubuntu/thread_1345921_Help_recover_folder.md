---
title: "Help recover folder"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by rhenium3 on 2009-12-04
Hi,

So I accidentally deleted a folder on my external hard drive.  I tried to find it in trash but nothing is there. When I dismounted the hard drive it asked me if I wanted to empty the trash. I said no. It dismounted. I re mounted it. Folder is still gone, still nothing in trash. Any help or is the folder lost?

I have ubuntu Karmic Koala....

Thanks in advance...

---

### Post by doas777 on 2009-12-04
well, one thing to try is to show hidden files. as I understand it, your external drive's trash shoudl be on the external drive at .trash-<username> or .trash-$<username>. just hit Ctrl + h to show hidden files.
if that doesn't work, look in ~/.local/share/Trash/files and see if anything turns up.

it also may be hidden in the trash folder, so be sure to use ctrl+h to check.

---

### Post by jbrown96 on 2009-12-04
It depends on your file system where the trash is located. I think Fat32 and NTFS both use a hidden folder name .Trash-100 where the number can be different. In the file browser, press Ctrl+H to show hidden folders. In ext3/4, there is a folder called Lost+Found, which is the trash.

---

### Post by lavinog on 2009-12-04
If you feel that you deleted the files, don't write to the drive.
Install testdisk which should install photorec
photorec can scan the raw sectors for the file you are missing and recover it.

---

### Post by rhenium3 on 2009-12-04
That totally worked!  Thank you SO much! :D

> **doas777 said:**
> well, one thing to try is to show hidden files. as I understand it, your external drive's trash shoudl be on the external drive at .trash-<username> or .trash-$<username>. just hit Ctrl + h to show hidden files.
if that doesn't work, look in ~/.local/share/Trash/files and see if anything turns up.

it also may be hidden in the trash folder, so be sure to use ctrl+h to check.

---

