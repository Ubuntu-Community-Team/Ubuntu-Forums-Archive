---
title: "How to delete &quot;floppy0&quot;"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by XeonBloomfield on 2010-12-21
Welcome

I had a floppy drive in PC, but yesterday I removed it.

Now in "Computer" in Nautilus I have this:
[[IMG]http://img697.imageshack.us/img697/9418/screenshot20jd.th.png[/IMG]](http://img697.imageshack.us/img697/9418/screenshot20jd.png)

[[IMG]http://img593.imageshack.us/img593/9137/screenshot21.th.png[/IMG]](http://img593.imageshack.us/img593/9137/screenshot21.png)

How can I remove it from this place and also from menu "Places"?

---

### Post by ibizatunes on 2010-12-21
sudo gedit /etc/fstab
the line that look simlar to this
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

put a "#" infront
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

reboot and your good to go!!

---

### Post by XeonBloomfield on 2010-12-21
Ok, but what file I need to modify?

// user above modificated his post, never mind

---

### Post by XeonBloomfield on 2010-12-21
Thank you. Problem solved. 

I marked thread as SOLVED.

---

