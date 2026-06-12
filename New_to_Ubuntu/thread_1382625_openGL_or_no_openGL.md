---
title: "openGL or no openGL?"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-16
I've got a vague idea of what openGL is from [wiki]("http://en.wikipedia.org/wiki/OpenGL"), but I'm confused as to whether it is implemented on my system or not. For example, I seem to have two variants of Cairo-Dock installed on my PC, one with openGL and one without it.

My question is, which of these should I set up? How do I find out which of them is right for my PC?

---

### Post by MelDJ on 2010-01-16
i think if you want the fancy graphics of cairo, you have to use the OpenGL version

---

### Post by 3rdalbum on 2010-01-16
If you have 3D acceleration, then you have OpenGL support. Basically, if you can run the Compiz visual effects, then you can run the OpenGL Cairo Dock.

If you have VIA, SiS or an older ATI graphics chipset that doesn't have any 3D drivers, then you'll need the non-OpenGL version of Cairo Dock.

---

### Post by fabounet on 2010-01-16
> Basically, if you can run the Compiz visual effects, then you can run the OpenGL Cairo Dock.
Unfortunately not. Cairo-Dock requires a complete OpenGL 2.0 driver; because Compiz doesn't need to be transparent since it draws the whole screen.
fortunately more and more drivers support it.

---

