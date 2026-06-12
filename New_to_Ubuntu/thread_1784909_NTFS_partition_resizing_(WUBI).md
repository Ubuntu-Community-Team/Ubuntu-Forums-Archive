---
title: "NTFS partition resizing (WUBI)"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by reelo2228 on 2011-06-17
Hey all! I Downloaded Ubuntu 11.04 yesterday and installed it with WUBI in windows( didnt read up on WUBI that time, and boy was i stupid)&#12290; I went crazy and started updating and installed conky, only then realised that the virtual memory allocated top the ubuntu WUBI install was REALLY small, so now i dont have "disk space" anymore (that partition still have additional 13gbs let shown in win7). I asked google, and this Gparted thingy came by saying that it could resize the partition for ubuntu. But now i'm scared that it may delete all the other files on hat same partition if i resize it( its NTFS btw). So i\d just like to confirm this, Or if there is any other better solution for it... And now i cant login to ubuntu anymore( maybe i ran out of disk space) a msg shown "the configuration defaults for GNOME power management was not installed correctly"


Thx A triple times Gazillion in advance!

---

### Post by Rubi1200 on 2011-06-17
Hi and welcome to the forums :-)

The safest and most reliable method of creating extra space for Wubi is explained in this thread:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by reelo2228 on 2011-06-17
still seemed quite risky to resize, the thread said that it MIGHT destroy al the data on the drive, so there i got discouraged >.>, ah man, i guess i have to reinstall ubuntu again. but THX!

---

### Post by Rubi1200 on 2011-06-17
There is always a certain amount of risk involved in such operations. However, if you make a copy of the current root.disk and put it somewhere safe like an external medium you can always restore it.

I also recommend you use the automated procedures outlined there as those are safer.

---

