---
title: "Cannot mount WD external harddrive as rw, please help"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by MS900 on 2009-02-25
I have a Dell 600m laptop running ubuntu 8.04 because I really hate windows, but i can't seem to get ubuntu to do the things I want it to.  I have a Western Digital external hd vfat and I can't seem to get it to stay mounted as read/write, I've tried everything I can think of and if I can't get this to work I think I'm going back to windows :'(

---

### Post by taurus on 2009-02-25
Assuming it's /dev/sdb1, you could do something like

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by Peter09 on 2009-02-25
Have you mounted it using fstab, if so what command did you use?

---

