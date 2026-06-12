---
title: "where the numbers are at"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by ianmaxwell on 2008-12-24
what specificaly does this mean? 'where the numbers are at'
do i just replace the numbers with those which i have?
copied from [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Insert the output of the uname -r command into the following 2 commands where the numbers are at

7. Gutsy Gibbon comes with this already installed so if you have Gutsy you can move to step 8.
Code:

sudo aptitude install linux-headers-2.6.22-14-generic

8.
Code:

sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build

---

### Post by ianmaxwell on 2008-12-24
uname -r

this  was the command i used to get the numbers 27-7

---

### Post by Old_Grey_Wolf on 2008-12-24
Yes, it is saying to replace the "2.6.22-14" with "2.6.27-7" in the two commands.

---

