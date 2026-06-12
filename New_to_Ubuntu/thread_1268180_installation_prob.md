---
title: "installation prob"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by navaneethan on 2009-09-16
when i am going to install any packages in my ubuntu hardy i face

> root@navtux-desktop:~# apt-get install gnome-desktop
[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]
root@navtux-desktop:~# apt-get install xfce
[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@navtux-desktop:~# sudo apt-get install --reinstall gnome-panel
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]


mainly these bolded problems

how to resolve this problem?

what is the reason?

---

### Post by sunchiqua on 2009-09-16
Computer restart should fix this problem. For the future knowledge, you can't use 2 APT sessions at the same time.

---

### Post by halitech on 2009-09-16
do you have synaptic open at the same time?

---

