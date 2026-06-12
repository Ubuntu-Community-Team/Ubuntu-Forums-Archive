---
title: "fstab error at startup"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-10-30
I am getting an error in my fstab while booting up that requires me to skip the "errored" mount to continue.  Nothing has changed in my fstab so I have no idea why this is happening.  When I choose to skip, I notice nothing different about what is mounted when I log in.  Does anyone have any ideas?

```
'# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=794c6ff5-df36-462e-a2db-6184f8f50618 /home           ext4    defaults        0       2
/dev/sdb3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/media/storage	auto	defaults	0	0
/dev/sdb2	/media/NTFS_Data	ntfs-3g	defaults	0	0
# Entry for andrew-server NFS share
# Note that you must create mount point /media/andrew-server
192.168.1.70:/media/data	/media/andrew-server	nfs	rsize=8192,wsize=8192,timeo=14,intr
#192.168.1.70:/home/andrew	/media/andrew-server_home	nfs	rsize=8192,wsize=8192,timeo=14,intr
```

---

### Post by baddnady23 on 2010-10-30
Haha I found it, I must have inadvertently hit the the ' key right at the beginning of fstab sometime while I was in it and it saved.  When trying to boot, it thought that it was a file system and obviously couldn't mount it.

---

### Post by Quackers on 2010-10-30
That might have something to do with it :-) Well spotted!

---

