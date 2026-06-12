---
title: "Problem with inconsistent splash screen"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-02-22
I'm using ubuntu 10.10  for some time now and lovin it....... I have an intel chipset ....the problem is I sometimes get a nice splash screen and sometimes a black screen with a curser dot....sometimes some text  before booting? why this inconsistency ?

---

### Post by deconstrained on 2011-02-22
Nothin's perfect. Especially if you use a proprietary graphics driver. 

The developers don't want to waste time perfecting a splash screen kernel patch for each and every different kind of graphics hardware, which often don't play fair (vendors don't release advanced specs for open-source development, so developing stuff for them is most often a shot in the dark). So they do it only for Noveau, the open-source, lower-performance graphics module, which is why when you boot to a live disk, you almost always get an amazingly beautiful, hi-res splash screen.

---

