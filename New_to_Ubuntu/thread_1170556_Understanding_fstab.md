---
title: "Understanding fstab"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-05-26
Okay Im new to Ubuntu but Im quickly trying to get my head round everything, but I cant figure this one out.  I have a partition /dev/sdb1 which I want to mount in my mount point /mnt/usb
So Ive used sudo to mount the drive but I cant get the permissions to read and write apparently due to the fact that its formatted as FAT32. After trawling through google pages I know to automatically mount it I have to add it to my fstab files, which now reads

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sdb1 /mnt/usb vfat defaults,user,exec,uid=999,gid=999,umask=000 0 2

The drive mounts but again it wont give me read write permissions.  What am I doing wrong??
Any help would be appreciated, Im pulling my hair out.

---

### Post by Elfy on 2009-05-26
closed - duplicate here [http://ubuntuforums.org/showthread.php?p=7349886](http://ubuntuforums.org/showthread.php?p=7349886)

---

