---
title: "JFS &amp; ext4 rw hotplug"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by s.kaniff on 2010-02-10
Hi,
I have a JFS formatted external drive. When I connect it, it always connects as a read only disk. Same thing happens if if format the disk to ext4. If I format the disk to NTFS then it mounts are read/write mode. I want a journaling file system on the external drive as I intend to run a VM off it. Is there any way I can get Ubuntu to mount external drives with EXT4 or JFS file systems in read/write mode?

---

### Post by aryan22 on 2010-02-10
Try

```
sudo chown -R $USER:$USER "/media/mount dir"
```Change the "/media/mount dir" to where your external disk is mounted.

---

### Post by s.kaniff on 2010-02-10
worked.. thanks.. :)

---

