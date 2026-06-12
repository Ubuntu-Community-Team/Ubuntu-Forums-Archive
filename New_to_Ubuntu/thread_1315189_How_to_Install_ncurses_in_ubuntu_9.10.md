---
title: "How to Install ncurses in ubuntu 9.10"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by harish4linux on 2009-11-05
I am trying to install ncurses using the command

apt-get install libncurses5-dev

then i get the following error please some body help me

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What i should do now...

---

### Post by nothingspecial on 2009-11-05
Have you got synaptic package manager, software center, gdebi or update manager open?

You can only use one at a time - inclunding apt-get, aptitude and dpkg.

---

### Post by desperado665 on 2009-11-05
use **sudo** apt-get install libncurses5-dev

---

