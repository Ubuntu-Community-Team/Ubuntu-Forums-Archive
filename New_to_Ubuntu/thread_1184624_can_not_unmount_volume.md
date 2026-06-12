---
title: "can not unmount volume"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by enri2 on 2009-06-11
I'm trying to unmount the cd drive, and it says that " I am not privileged to unmount the volume, only root can unmount." any ideas? this happened after installing vuze

---

### Post by TeoBigusGeekus on 2009-06-11
Happened to me from time to time during the Hardy Heron era.
Just type:
```
sudo umount /dev/scd0
```
or whatever device your cd is.

EDIT:
Anyway, if Vuze is giving you so much trouble (this must be your 3rd thread about it right?), why don't you use KTorrent, Tranmission, Deluge, etc.?

---

### Post by enri2 on 2009-06-11
thanks

---

