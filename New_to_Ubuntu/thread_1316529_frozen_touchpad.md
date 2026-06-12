---
title: "frozen touchpad"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by artandactivism on 2009-11-06
I downloaded and installed Ubuntu 9.10 a few days ago and since then my touchpad cursor is frozen in the middle of the screen. I tried an external mouse and that works, but I much prefer using the touchpad. Has anyone else had a similar problem? Thanks

---

### Post by jimmy the saint on 2009-11-06
Give us some information about your hardware

---

### Post by Plumtreed on 2009-11-06
I have had a similar prob but I 'updated' which caused a conflict of some sort with Grub/Grub2. I ended up with the new Karmic trying to run in the old 9.04 kernel. Once I got Grub2 sorted everything runs perfectly especially the touch-pad problem.

Check on boot-up or via System Monitor.....should be 2.6.31 -14

---

### Post by artandactivism on 2009-11-06
I'm getting the following error in the Xorg logfile.

SynPS/2 Synaptics TouchPad The /dev/input/event* device nodes seem to be missing

I think I'm running the latest kernel -  2.6.28-13-generic

It's a Samsung R522 laptop.

Any other thoughts?

---

### Post by artandactivism on 2009-11-06
Ah. Enabling kernel 2.6.31-14-generic as default did resolve the issue. Thanks everyone.

---

