---
title: "software center opens and goes"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by ravi sharan on 2011-03-27
hi, 
i m using ubuntu 10.04 since recently. suddently my software center or anything related to software center is not opening properly... can anyone let me kno how to solve this ? i m enclosing the error msg shown :

/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()
Segmentation fault

can anyone let me know wat actually the problem is ???

---

### Post by vivek.pandey on 2011-03-27
on terminal type this
sudo gedit /usr/share/software-center/softwarecenter/apt/aptcache.py

and post the contents of the file

---

