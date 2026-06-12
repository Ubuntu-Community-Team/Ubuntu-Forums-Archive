---
title: "Reinstalling after failed install."
date: 2008-12-09
forum: New to Ubuntu
---

### Post by dav1dc on 2008-12-09
I an new to Ubuntu (& Linux), but after obtaining an Ubunto 8.10 CD, and trying out before installing, and liking what I saw, I tried installing on a Windows PC running XP, with 80GB HD and plenty of free space. The installation seemed to be going OK, disk partitioned, but the installation did not complete as it could not read one file on the CD.

(I understand this may be a problem with the optical drive, and I am considering getting another to try out.) However, that is not my only question.

I have tried installing again, but stopped at the section where the HD is partitioned, not wanting to proceed because the installation program wants to repartition the HD again, adding still more partitions, but not using those created by the failed installation. 

So my question is: Is it possible to reinstall onto the partitions created by the failed install or is it possible to erase those partitions prior to trying a new clean install? If so, how?

---

### Post by stephanvaningen on 2008-12-09
You can choose a manual partitioning at that point. On the next screen you will see a list of the partitions existing on the 80GB HDD.

Edit the partition listed as 'ext3' and change the mount point to '/', also check the checkbox for formatting.

That should do it, it will probably automatically find the already existing swap-partition if you can not change the settings of it on that same screen.

---

### Post by mapes12 on 2008-12-09
> Is it possible to reinstall onto the partitions created by the failed installPost #2 addresses this but not easy for a newcomer.

> or is it possible to erase those partitions prior to trying a new clean install? If so, how? Yep.If you have a Live CD boot it then run an application called GParted to manage your partitions. Alternatively. you can make a GParted Live CD from [here]("http://gparted.sourceforge.net/").

---

### Post by mapes12 on 2008-12-09
> Is it possible to reinstall onto the partitions created by the failed installPost #2 addresses this but not easy for a newcomer.

> or is it possible to erase those partitions prior to trying a new clean install? If so, how? Yep.If you have a Live CD boot it then run an application called GParted to manage your partitions. Alternatively. you can make a GParted Live CD from [here]("http://gparted.sourceforge.net/").

---

### Post by dav1dc on 2008-12-10
Thanks for those replies, I will try out your suggestions and report the results.
:p

---

