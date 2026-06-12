---
title: "Changing mount point name"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by MattM11 on 2009-10-06
I recently installed Xubuntu, and used NTFS Configuration Tool to mount my 2 NTFS partitions. Stupidly, I managed to use the wrong names as the mount point (So my vista partition is labeled as my data partition, and vice verse). This isn't a huge problem, but I was wondering if there was anyway to rename the mount points...

Any help would be much appreciated.

---

### Post by sisco311 on 2009-10-06
the mount points are stored in the /etc/fstab file.

edit the file:
```
gksu mousepad /etc/fstab
```

you should see something like:
```
/dev/sdXY    **/media/data**    ntfs    defaults[,...]    0     0
/dev/sdXZ    **/media/vista**    ntfs    defaults[,...]    0     0
```

invert the mount points and remount the partitions:
```
sudo umount /media/vista
sudo umount /media/data
sudo mount -a
```

---

### Post by MattM11 on 2009-10-06
Great - that seems to have done the trick. Thanks.

---

