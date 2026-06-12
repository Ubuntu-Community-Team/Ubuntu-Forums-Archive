---
title: "access other drives or partitions"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Norman Thom on 2010-01-08
I am just trying out Kubuntu 9.10 for the first time. (Dual boot with XP)
Unlike Ubuntu I get no access to my other drives on the computer.
Does anyone know how I can resolve this problem I would like to get into my other drives for information that is stored there

Thanks

Norm

---

### Post by aaronp on 2010-01-09
> **Norman Thom said:**
> I am just trying out Kubuntu 9.10 for the first time. (Dual boot with XP)
Unlike Ubuntu I get no access to my other drives on the computer.
Does anyone know how I can resolve this problem I would like to get into my other drives for information that is stored there

Thanks

Norm

Did you change your existing Ubuntu to Kubuntu or install Kubuntu fresh?
If you just applied KDE over your existing Ubuntu install then the other drives should still be mounted as per usual, they may just not be appearing like you are used to.
Try typing ```
mount
``` into a terminal and see if the ntfs volumes are mounted. You should then be able to access them by their mountpoint listed in the output of the command.
(e.g. /media/XXXXX or /mount/XXXXX)

---

### Post by GameManK on 2010-01-10
When you open up Dolphin, are there no drives listed on the left side?

Also, there is a plugged in devices applet in the panel, if you click on that, does that list anything?

---

