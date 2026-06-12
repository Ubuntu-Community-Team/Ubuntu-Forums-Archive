---
title: "GEOM error"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by gronater on 2010-12-28
Hello,

I've got an error when starting up my pc, it says:

GEOM error

Reboot and select proper disk device

I tried with F8 to select other boot devices and changed boot device in bios but it didn't work. I reinstalled my windows 7 and then ubuntu 10.04, got the same error.
Maybe usefull:
My Windows is on sda1, home folder on sda2 and swap on sda3.
sdb1 is data and sdb2 is ubuntu /boot

Searched google and stuff but nothing really pointed out to help.

Hope you can help me,

Gronater

---

### Post by davidmohammed on 2010-12-28
I presume you found [this thread]("http://ubuntuforums.org/showthread.php?t=1374209") which contains advice on this error?

---

### Post by gronater on 2010-12-28
Pff never found that one, will probably take a few days to fix it.
But can I edit /etc/fstab and install lilo etc if I use ubuntu from a live cd, because I can't run my installed ubuntu...

edit:

I need to be root to edit fstab, that's probably als the prob why gksudo gedit /etc/fstab didn't work. How can i become root on a live cd?

next edit:

I really need some help, how can I become root on a live-cd? I typed su in the terminal and typed my installed ubuntu password, but it says "authentication failure". I can't edit fstab without root acces!

---

