---
title: "ubuntu on virtualbox : issue with nvidia and glx"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by bbforum on 2010-09-02
[LEFT]Hi,
[/LEFT]


I installed ubuntu 10.04 on a virtual machine (on virtualbox) and added the "Guest Additions". At this point glxgears works, but the graphical interface isn't refreshed any more.

I then installed the nvidia drivers (nvidia-glx-185). The graphical interface works now fine, but glxgears doesn't work any more :
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

If I remove nvidia drivers, I'm in the first case again.

The problem is that I need glx to be working (for one of our program), but if the nvidia drivers are not installed, the graphical interface issues make it impossible to work with this program.

Is there a way to make glx work with nvidia on virtualbox ? Or is there a way to have the graphical interface work fine without nvidia drivers ?


Thanks in advance.

---

