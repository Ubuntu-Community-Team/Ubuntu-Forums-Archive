---
title: "smbfs mnt only accesible by root"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by byenary on 2010-07-26
Hello,

In a script I mount an external smbfs like this
mount -t smbfs //192.168.123.6/Data /mnt/data3 -o username=user,password=fasdgasf
Now this folder /mnt/data3 automaticly becomes property from root and cant seem to change permissions of it.
Is there a way to make this folder accesible for other user on the system where it is mounted ?

Regards.

---

### Post by tarps87 on 2010-07-26
Is there any reason you use a script on fstab?

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

