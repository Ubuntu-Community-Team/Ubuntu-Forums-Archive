---
title: "Display problem - sizing"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by jessedavis on 2010-10-08
Ubuntu 9.04 nVidia display card. Resolution 800 X 600 (determined by the display hardware) Gnome desktop with default window manager.  The problem is that while many programs display correctly (gedit, Firefox, etc.) there are a few that do not (evolution mail, pcb).  In evolution is is not possible to resize the panels in the main window.  The correct pointer appears; however, I can not grab the frame. It is as thought the display is locked.  This leaves the side (files) panel too small to be useful.  In pcb the display is about 25% wider than the screen.  One can make it bigger but not smaller.  none of the obvious fixes (alt + F8, alt + Space, etc.) will fix the problem.  I have verified that the physical display resolution and the system display resolution are the same.  I can drag the panels left, right, up & down and see everything.  I just can't resize them.

Any thoughts on what I am doing wrong?

---

### Post by cariboo on 2010-10-08
Are you using the restricted graphics driver? or is 800X600 the maximum your display will do?

---

### Post by jessedavis on 2010-10-09
> **cariboo907 said:**
> Are you using the restricted graphics driver? or is 800X600 the maximum your display will do?

The display is the limit. Something else I have noticed is the PCB Designer program has an preference file; however, I cannot change the display size to a lower value.  Each time I change it and run PCB Designer the preference file is returned to the previous value or if I resize the window to a LARGER size the preference file will reflect the last used window (larger)size.  I would appear that the window size is set to a hard limit of 938 pixels.  Why anyone would do that I can't say.

---

