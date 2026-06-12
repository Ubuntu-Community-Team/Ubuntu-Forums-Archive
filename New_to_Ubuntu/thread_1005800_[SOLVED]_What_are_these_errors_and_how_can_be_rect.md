---
title: "[SOLVED] What are these errors and how can be rectified?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ellalan on 2008-12-08
Hi
When I type opera in terminal I get these error messages(view the attachments) could someone please tell me how to correct them. TIA.

---

### Post by gettinoriginal on 2008-12-08
It looks like you do not have opera installed, or if you do, not correctly.  Check synaptic to see if you have it installed, and if so, uninstall it and then reinstall.

---

### Post by ellalan on 2008-12-08
Hi,
Thank you for the help, I tried uninstalling the version 9.62 which was installed from Opera site and installed the version 9.27 which is in synaptics but I do still get the same message.

---

### Post by gettinoriginal on 2008-12-08
Now that you have it installed, it should be under Applications > Internet try opening it from there and see what happens

---

### Post by ellalan on 2008-12-09
Opera is working but I am curious what those errors mean. Thanks.

---

### Post by jamesrl on 2008-12-09
libjvm is library for the java virtual machine.
libawt is the abstract window toolkit (which is also associated with java).
The shared libraries cannot be preloaded for some reason.  Do you have sunjava installed?
ZPixmap message is just a warning message about opera not thinking your X configuration supports shared memory with zpixmap.  I wouldn't worry about it.
[http://pantransit.reptiles.org/prog/mit-shm.html](http://pantransit.reptiles.org/prog/mit-shm.html)

---

### Post by ellalan on 2008-12-09
I couldn't see any java installed in synaptics, could you please tell me which one I should install.

---

### Post by Pjotrovitz on 2008-12-09
If you only need to run java files you could install the sun-java6-jre package.

---

### Post by stevoo on 2008-12-09
what he said :) :P

---

