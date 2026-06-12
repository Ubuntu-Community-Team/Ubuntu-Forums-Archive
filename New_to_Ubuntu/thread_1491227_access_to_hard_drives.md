---
title: "access to hard drives"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by moliel on 2010-05-23
When booting ubuntu from a CD or usb device I don't have write permission to hard drives. Is there a way to change that ?
Please help
Thanks
Mickey

---

### Post by Skorzen on 2010-05-23
Which drives do you want to access?

With 'root' permissions you'll be able to do everything you want. Even changing permissions on those drives, that would be what I'd recommend.

Post the output of:
```
df -H
```
```
cat /etc/fstab
```

---

### Post by moliel on 2010-05-23
I'm trying to access an external drive but I have the same problem with the internal hard disk also.
I'm using root and I can't change the permission for that drive because it's "Read-only file system"
df -H
gives the list of file system. The line for the disk I need is:
( Sorry I can't cut and paste I need to type it)
/dev/sdc1      1.1T   70G  931G  7% /media/FV-U35


cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


Does this make sense ?

---

### Post by moliel on 2010-05-26
Anyone have any idea what I'm doing wrong ?

---

