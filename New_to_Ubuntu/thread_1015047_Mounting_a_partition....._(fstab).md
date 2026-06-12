---
title: "Mounting a partition..... (fstab)"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-12-18
So I set up a partition on my HDD as fat32 so that both my windows install and my ubuntu install can access it, only problem is that it mounts as read only unless I'm root....

Current fstab line to mount it is:
/dev/sda4	/media/tinypartition	vfat	user,auto,exec,rw	0	0

I thought the 'user' line was supposed to allow me to access it as a user, I also tried 'nouser' with the same results??

---

### Post by Elfy on 2008-12-18
Try this, from here - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

```
/dev/sda4 /media/tinypartition vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

---

### Post by danielpalos on 2008-12-18
You may want to try a windows emulator instead.  You can install a windows emulator (wine) from system/add remove menu and then run them from that application.

---

### Post by Duck2006 on 2008-12-18
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

