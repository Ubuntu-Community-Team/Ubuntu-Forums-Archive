---
title: "Intel 82852/855GM Graphics Problem"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by SyntaxError77 on 2009-12-18
I'm using Karmic Koala 9.10 on an IBM ThinkPad R50e. I have the desktop effects enable so when a window is dragged it has an elastic look.
 
But when I compile and run an OpenGL application that renders a single square with a texture on it, it runs incredibly slowly, 1 frame every few seconds.
 
I can run the same code on my home pc with an NVidia card and it runs super fast.
 
How can the desktop effects work, but not a simple textured cube?
 
Also, is there a driver I should be using? I have searched Synaptic for Intel drivers, but I cannot see anything useful there.
 
Any help would be appreciated.
 
Thanks
 
Paul

---

### Post by northern lights on 2009-12-18
Are you sure that that's not an issue of CPU load?

Run```
top
```while running the OpenGL app to check.

---

