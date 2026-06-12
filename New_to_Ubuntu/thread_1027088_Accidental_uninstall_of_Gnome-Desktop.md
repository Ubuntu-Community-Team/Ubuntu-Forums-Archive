---
title: "Accidental uninstall of Gnome-Desktop"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by emocontrol on 2008-12-31
I was trying to get multiple wallpapers in the cube using this method.
[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)
And it uninstalled Gnome-Destkop, now I cant open up "Computer".
I went into terminal and am currently installing Gnome. Will that fix it?
Im in Intrepid Ibex by the way. Oh and still no multiple wallpapers in the cube :[

---

### Post by 5BallJuggler on 2008-12-31
you will have to remove compiz and I think the desktop will come back, i had a similar issue.

I cant remember the exact code, but it's something like

to open your terminal press Ctrl+Alt+F1

sudo apt-get install remove compizfusion

good luck

---

### Post by abn91c on 2008-12-31
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by 5BallJuggler on 2008-12-31
I was close......
.....ish

that's what happens after a night of drinking.

:lolflag:

---

### Post by adult swim on 2008-12-31
one of the things you did when you followed that tutorial was to uninstall nautilus which, among other things, is the file manager for ubuntu.  a few steps down you are building a patched version of nautilus.  if there were any errors in building the patched version, that leaves you with no nautilus and thus you cant access "computer"  my advice would be to run ```
sudo apt-get install nautilus
``` im not sure but you may have to log out and log back in again for it to fire up.

---

