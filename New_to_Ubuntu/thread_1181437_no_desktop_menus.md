---
title: "no desktop menus"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by almagr on 2009-06-07
I installed ubuntu y.day no problem.  I made  a few basic changes to the desktop.  Added a desktp pic and changed a few of the items in the drop down menus.  Nothing major.  The nest day.  My desktop has the desktop background and the one icon I wanted on the desktop.  Nothing else at all is visible.  And i cant access termainal, as theres no menu for it and f2 doesnt work.  Please help

---

### Post by konqueror7 on 2009-06-07
try this,
- ctrl + alt + f1 (or f2 until f6), this will get you to a terminal
- login to it, nad type "gnome-panel"
- switch back by pressing, ctrl + alt + f7

or,
- right-click at your desktop
- create a application launcher, set the command as "gnome-terminal"
- a launcher will be created, launch it and type "gnome-terminal & disown"

---

### Post by almagr on 2009-06-08
the gnome panel in terminal brings the menus/panel back, but they go when terminal is closed

---

### Post by konqueror7 on 2009-06-08
have you tried the 2nd method?

try this,
- do 1st method
- now, don't logout from the terminal, just switch to ctrl + alt + f7
- add "gnome-panel" to you sessions/startup applications...

---

### Post by almagr on 2009-06-08
that worked. cheers:D

---

