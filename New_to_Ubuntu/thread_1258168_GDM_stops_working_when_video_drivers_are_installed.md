---
title: "GDM stops working when video drivers are installed"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by ZukaZuka on 2009-09-04
Using Ubuntu 9.04, Jaunty Jackalope.
 
I recently installed the latest video driver for my cards (NVIDIA GeForce 8600GTSx2), and restarted. When I started it again, I got the terminal login, not the GUI. I cannot get the GUI to work.
 
I've tried...
 
```
sudo /etc/init.d/gdm start
```
 
It tells me it's starting, but CTRL+ALT+F7 just reveals a blank screen, sometimes with a blinking underscore (keyboard input does nothing here).
 
```
sudo init 3
```
```
sudo init 5
```
 
Everything my friend told me to do. I've reinstalled, restarted, everything. I even tried editing "/etc/X11/xorg.conf", adding the BusId and Option entries to the Device section (BusId from lspci, Option being "SLI" "SFR".)
 
What else is there to do? I have two monitors, is that affecting it? Only one works at the moment...
 
I'm getting really fed up with computer problems...

---

### Post by ZukaZuka on 2009-09-04
Is this in the right place?

---

### Post by ZukaZuka on 2009-09-04
So, can no one help me?

---

### Post by NoaHall on 2009-09-04
Right, I'll give you two options - install 8.04 instead (it has better support for these kind of problems) or remove your nvidia driver and run ubuntu without it.

---

### Post by ZukaZuka on 2009-09-05
I installed 8.04. The NVIDIA drivers work, but only on one monitor. It won't even detect them, and the one it does is "Unknown".

---

