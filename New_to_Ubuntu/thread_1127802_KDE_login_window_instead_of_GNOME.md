---
title: "KDE login window instead of GNOME"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-16
I have Ubuntu with KDE added, and have pretty much switched to KDE, though Gnome still has its uses.  Anyway, I have a custom Gnome themed face browser, and I would like to use the KDE default.  How to I do this?  Gnome seems to be in control...

---

### Post by Hendronicus on 2009-04-17
Open the terminal and paste in :

sudo dpkg-reconfigure gdm

and it should ask you which display manager you want to use. Then, logout and when you see the kdm screen remember to change your session to KDE as well.

---

### Post by qwertyuiop96 on 2009-04-17
> **Hendronicus said:**
> Open the terminal and paste in :

sudo dpkg-reconfigure gdm

and it should ask you which display manager you want to use. Then, logout and when you see the kdm screen remember to change your session to KDE as well.

Worked fine, thanks.

---

