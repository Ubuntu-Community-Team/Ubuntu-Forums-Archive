---
title: "White Screen of Death - One Solution"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by wkrik on 2008-12-11
I jut ran into this issue. In my instance it was after my system froze and I was forced to power cycle the system. When I tried to login, the *white screen of death* was displayed. Somthing to note, the system wasn't dead, after 5 min it went into the screen saver. It appeared that a package somewhere int he system got corrupted somehow so here is what I did:

At the login screen, select: Option / Gnome-failsafe
From a shell: 
$ sudo apt-get update
$ sudo dpkg --configure -a
$ sudo apt-get install -f
reboot

When it came back all was fine.

-Good luck

---

