---
title: "drive mount"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by brijraj22 on 2010-07-07
how do i force mount a drive, in which ntfs is marked in use (unclean shutdown)?

---

### Post by johngreth on 2010-07-07
can you remove the flag with gparted or another partition/drive manager?

---

### Post by vysotsky on 2010-07-07
What happens when you try to mount it from the terminal?  Have you tried to mount it with this:

sudo mount -t ntfs-3g [something like /dev/sda1] [something like /media/windows] -o force

---

### Post by brijraj22 on 2010-07-08
sudo mount -t ntfs-3g -o force /dev/sda3 /media/windows 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/windows: No such file or directory
;)

---

### Post by tarps87 on 2010-07-08
> **brijraj22 said:**
> sudo mount -t ntfs-3g -o force /dev/sda3 /media/windows 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/windows: No such file or directory
;)
Run this first
```
sudo mkdir /media/windows
```

---

