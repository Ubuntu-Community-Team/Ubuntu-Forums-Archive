---
title: "init file"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-10
Has anyone ever changed their init file so a differnet runtime loads upon a boot (say runtime 3)?  If so, worth messing around with (obviously carefully) for experience sake?

---

### Post by Geoff918 on 2009-12-10
No, I haven't. But honestly, why would you want to?

Runlevel 5 is perfectly fine.

Is there some reason you'd like to enter a different runlevel?

I sometimes do. I will sometimes init0 my machine to shutdown or maybe init6 it to reboot, but other than that I've never had cause to change runlevels.

---

### Post by sweet_cogito on 2009-12-10
Not really all that useful, basically just runlevel 5 for X, runlevel 3 for standard text shell.  Just stay away from runlevel 0 and 6 as 0 will shutdown, and 6 reboots.  Have fun!

---

### Post by Diametric on 2009-12-10
Thanks for both of your replies...just working my way through a Linux book.  Is there a way to access X from gnome, without changing init?  Also, upon reboot, the init file goes back to the previous state (state 5?)..yeah?

---

### Post by falconindy on 2009-12-11
X is what Gnome displays itself on. Its the basis of the graphical environment. The Gnome packages are worthless without X.

In most Linux systems, runlevels aren't really significant. They're more important to embedded devices where you need/want a finer level of control over what programs are running in order to fine tune your power consumption.

---

### Post by Geoff918 on 2009-12-11
You'll catch on quick. X runs the basic graphical display upon which pretty much else is built.  gdm is the GNOME display manager (I'm pretty sure).

You can change around what runs on what. You could run enlightenment instead, there are other window managers such as fluxbox or jwm or lxde. There are tons of different options all with their own strengths and weaknesses. Some are heavier, some are lighter but uglier as well, lol.

Anyway, there are lots of good guides. Perhaps your book might explain some more, too.

---

