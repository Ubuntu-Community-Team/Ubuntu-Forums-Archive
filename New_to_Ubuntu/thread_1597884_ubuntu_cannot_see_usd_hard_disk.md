---
title: "ubuntu cannot see usd hard disk"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by paker on 2010-10-15
The usb hard disk was formatted ntfs with a windows machine. Now ubuntu cannot see it. Solution?

gparted doesn't list the usb hard disk.

---

### Post by papibe on 2010-10-16
In my experience, there's a few external usb hard drives that are not auto mounted in Ubuntu. First thing I would try, is to check if it was at least recognized using some or all of the following commands:
```
$ lusb
$ sudo fdisk -l
```
If you can see the device (e.g. /dev/sdb1) you can mount it manually:
```
$ mkdir mnt
$ mount /dev/sdb1/ mnt
```

In the case it didn't get recognized you can try to restart your PC with the usb disk powered up and connected.

Good Luck!

---

### Post by paker on 2010-10-16
Thank you for the manual mounting method.

---

### Post by laithbsoul on 2010-10-16
you can also check disk utility it should still show in there and you can click mount. if you want to stay away from the terminal? either way works the same though.

---

