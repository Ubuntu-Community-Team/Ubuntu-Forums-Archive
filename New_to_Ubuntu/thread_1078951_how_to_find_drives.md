---
title: "how to find drives"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Mitch9654 on 2009-02-23
I want to find out what letter my cd drive is (for DOSBox)

mitch96

---

### Post by ptn107 on 2009-02-23
Ubuntu (and linux in general) does not assign drive letters like windows did.  Instead your cdrom drive /dev/scd# is mounted to a folder in /media/cdrom# where your system can access it*.  So your cdrom is not at drive D: or whatever, it's at /media/cdrom0.

* If you only have one drive it's /dev/scd0 mounted to /media/cdrom0.  Those numbers increase for each drive you have.  Also note that /media/cdrom is always a symbolic link to your first cdrom (/media/cdrom0) drive.

If your just wondering how dosbox sees your cdrom, it's usually drive D:\.
[http://www.dosbox.com/wiki/MOUNT](http://www.dosbox.com/wiki/MOUNT)

---

