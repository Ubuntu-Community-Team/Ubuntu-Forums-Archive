---
title: "Mounting drive"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2010-10-02
whenever i start ubuntu, i have to mount all the drives individually. Is there any method that i can make the drive mount automatically when ubuntu boots??

---

### Post by Troublegum on 2010-10-02
sure, specify your mount points in /etc/fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by ibuclaw on 2010-10-02
You can add the mount entries to /etc/fstab - you'll require super-user privileges to edit that file, so be sure to use 'sudo' or 'gksudo'

There are plenty of guides explaining fstab around, but if you nee any clarification on what to do, just post back.

Regards
Iain

---

