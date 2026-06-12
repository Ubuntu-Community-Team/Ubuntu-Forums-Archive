---
title: "Backup question"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by cygnis1 on 2009-10-02
I have decided to backup my home directory on an external hard drive, and have purchased a Western Digital Passport usb external drive,formatted with ntfs.  Should I reformat the external drive to ext 3? Or ext 4?  I am currently using Hardy, but will upgrade to Karmic when it is available.  I understand that Karmic will by default use ext 4.  I am going to create a separate partition for my home directory.  If I use ntfs or ext 3, will the directory be automatically converted to ext 4? 
Thanks for any help,
Cygnis1

---

### Post by Paqman on 2009-10-02
> **cygnis1 said:**
> Should I reformat the external drive to ext 3? Or ext 4?


Yep, why not. It makes sense to use a native Linux format with a Linux system. Ext4 is faster, but less mature than ext3 (although it is stable)

> 
I am currently using Hardy, but will upgrade to Karmic when it is available.  I understand that Karmic will by default use ext 4.  I am going to create a separate partition for my home directory.  If I use ntfs or ext 3, will the directory be automatically converted to ext 4? 


Karmic will only use ext4 by default for any newly created partitions. A partition that's already on your disk won't be converted.

---

### Post by LewRockwell on 2009-10-02
Clonezilla

.

---

