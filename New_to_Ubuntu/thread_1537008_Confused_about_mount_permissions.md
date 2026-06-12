---
title: "Confused about mount permissions"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by alimnios72 on 2010-07-23
Hi, 

I have a shared NTFS partition between my two OS Ubuntu 10.04 and windows 7. When I mount this partition using the places menu, Ubuntu gives rwxrwxrwx permission to files and drwx------ permission to folders. I tried to use chmod command to change permissions to the folders (in oder to write or delete) but it isn't working. 

I read a little bit and found how to edit fstab and did the following:

/dev/sda2 /media/SHARED ntfs-3g quiet,defaults,rw 0 0

Now my partition is mounted automatically when I boot my PC but now folders and files have all permissions rwxrwxrwx and I can not change this using chmod. So my question is: is there a way to mount my partition with different permission in files and folders?
I want some folders to have all permissions, some others just root permissions, some files executables, some not, etc. how can I avoid same permissions on all folders and files?

Thanks

---

### Post by mcduck on 2010-07-23
Sorry, but no. NTFS (and FAT) doesn't support file ownerships and permissions as they are used in Unix/Linux operating systems. So they have absolutely no way to handle or store these permissions. Because of this, the permissions are simply set for the whole partition at the time it's mounted, and you can't change them on individual files/directories.

The only way around this is to use some other file system than those two.

---

### Post by alimnios72 on 2010-07-23
Thanks mcduck, when you mention FAT this also applies to FAT32 filesystem?

---

### Post by mcduck on 2010-07-24
> **alimnios72 said:**
> Thanks mcduck, when you mention FAT this also applies to FAT32 filesystem?

Yes, any versions of FAT and NTFS filesystems.

---

