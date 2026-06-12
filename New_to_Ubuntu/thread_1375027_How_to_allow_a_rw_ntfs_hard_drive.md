---
title: "How to allow a r/w ntfs hard drive"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by josephellengar on 2010-01-07
I recently bought myself an awesome dv7t quad edition, which happens to have two hard drives.  I am trying to set up the second hard drive in the fstab, but am having a little bit of trouble.  I have the second hard drive (which is /dev/sdb1) formatted to ntfs so windows can view it as well (I can't use vfat because of the 2gb filesize limit) but I get the following error:
```

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```
This is what my fstab is:
```

/dev/sdb1 /home/ross/storage ntfs user,rw 0 0

```

When I tried it with ext4 it mounted but was read-only.  If you can suggest a way to do this with ext4 I would be willing to use that fs.  Thank you!

---

### Post by Elfy on 2010-01-07
Try

```
/dev/sdb1 /home/ross/storage ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

[https://help.ubuntu.com/community/Fstab#File%20System%20Type](https://help.ubuntu.com/community/Fstab#File%20System%20Type)

---

### Post by josephellengar on 2010-01-07
This is what I tried with the hard drive being formatted as ext4:
```

/dev/sdb1 /home/ross/storage ext4 user,rw 0 0

```
There were no errors mounting it, but it was read only.  Any ideas?

---

### Post by josephellengar on 2010-01-07
> **forestpiskie said:**
> Try

```
/dev/sdb1 /home/ross/storage ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

[https://help.ubuntu.com/community/Fstab#File%20System%20Type](https://help.ubuntu.com/community/Fstab#File%20System%20Type)

Thank for your help, but unfortunately I got this error:
```

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

---

### Post by josephellengar on 2010-01-07
Never mind.  I forgot to reboot.  It's working now.  Thanks for your help!

---

