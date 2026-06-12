---
title: "wheres my nfts partition ?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-12-04
how come i cannot see or access my windows vista partition in xubuntu ? i cant even find it to mount it, i know it was there when i had ubuntu. is there a command i need to use to have it recognized and automounted ? :o

---

### Post by cdmike2k8 on 2008-12-04
Could you post the output of ```
sudo fdisk -l
``` to see if the drive is showing up at all?

---

### Post by smooth3006 on 2008-12-04
> **cdmike2k8 said:**
> Could you post the output of ```
sudo fdisk -l
``` to see if the drive is showing up at all?
as soon as i reinstall ill post it. i heard xubuntu doesnt pick up nfts without a command or program installed ? is that true ?

---

### Post by cdmike2k8 on 2008-12-04
I would believe that you could see it, although I don't know for sure, although getting ntfs-3g might help if you can't see it, since it is a ntfs file system.

---

### Post by Paqman on 2008-12-04
> **cdmike2k8 said:**
> I would believe that you could see it, although I don't know for sure, although getting ntfs-3g might help if you can't see it, since it is a ntfs file system.

Ntfs-3g has been included in the default install for some time now.

**smooth3006**: there's a good package called ntfs-config that should find and mount your NTFS partition easily.

---

