---
title: "Add a UUID to /etc/fstab"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Dark006 on 2009-02-16
I'm just wondering what the easiest way to add a UUID to /etc/fstab is. I have a backup script that uses rsync  daily and it always saves it to /media/disk-1. Is there a way to make the UUID of my external drive always mount as /media/disk-1?

The UUID for my external is 
```
/dev/sdf1: UUID="0203454e-4064-4cb0-a837-338ff5c30c3b" TYPE="ext3"
``` 

Thanks for any help.

---

### Post by bodhi.zazen on 2009-02-16
manually edit /etc/fstab and add

UUID=xxx.yyy.zzz

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

