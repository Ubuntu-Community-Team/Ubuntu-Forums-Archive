---
title: "how to fix duplicate source"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-03-20
how do i fix this error


Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

note apt-get update does not fix

tks

---

### Post by themusicalduck on 2010-03-20
Go to System > Administration > Software Sources.

Find one of the duplicate sources and remove it from the list.

Alternatively use ```
sudo gedit /etc/apt/sources.list
``` and delete the line off that file.

---

### Post by rburkartjo on 2010-03-20
tks the that did the trick

---

### Post by 2hot6ft2 on 2010-03-20
> **rburkartjo said:**
> tks the that did the trick
Putting solved and thank you as tags is interesting.
The way to mark the thread as solved is to click on Thread Tools at the top of the thread and select Mark as Solved.
:lolflag:

---

