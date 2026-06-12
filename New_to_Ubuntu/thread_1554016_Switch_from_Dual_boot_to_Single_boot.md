---
title: "Switch from Dual boot to Single boot"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by ajdrew06 on 2010-08-16
Hi All,

I use Ubuntu 9.04 as my main OS, and I wanted to try 10.04 a try.  I installed 10.04 side-by-side, so I opt which version I want when I boot.  Now, I am satisfied with 10.04, and I was wondering if there is a way to get rid of 9.04 without reformatting the entire drive.  

Thank you!

---

### Post by diablo75 on 2010-08-16
Best thing to do is download a copy of Gparted and use it to delete the partition that houses your copy of 9.04.  Be sure you delete the correct one.  Then use Gparted to stretch the size of your 10.04 partition out to fill in the gap created by deleting the old system.

This will likely take Grub out for the count when you do this and you'll need to reinstall grub using a 10.04 Live CD.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Having said that... if I were you, I'd format and start from scratch because it will take far less time to do that, not counting the time to backup personal data before starting from scratch.  If you need motivation for formatting instead of deleting the old and resizing the new, just take a look at that second link above.  Just my opinion, but setting grub up after it's been wiped out is kind of a pain.  Sometimes the easiest route is also the best, but it's up to you.

---

### Post by ajdrew06 on 2010-08-16
Hi diablo75,

I downloaded GParted, and I deleted the partition with 9.04.  I don't know how to stretch the partition with 10.04.  Perhaps, you could help me with this further!  Thank you!

---

### Post by wilee-nilee on 2010-08-16
> **ajdrew06 said:**
> Hi diablo75,

I downloaded GParted, and I deleted the partition with 9.04.  I don't know how to stretch the partition with 10.04.  Perhaps, you could help me with this further!  Thank you!

Post a screenshot of gparted.

---

### Post by oldfred on 2010-08-16
I would suggest converting the space to /home or /data and not moving your existing install.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

