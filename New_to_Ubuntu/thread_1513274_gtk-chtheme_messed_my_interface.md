---
title: "gtk-chtheme messed my interface"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by gianluca.pettinello on 2010-06-19
Hello everybody,
two days ago, after installing gtk-chtheme, I tried to change the theme in System-Preferences-Appearance. I chose dust sand but the graphics was messy and compiz very slow. I come back to Ambiance but some details of the decorations were strange (form of buttons, menu separators) and above all the speed of animations was incredibly low. Besides the output screenlet, which normally is transparent, becomes opaque as if compiz had a problem.
I tried to uninstall the gtk engines, to reinstall compiz, to uninstall gtk-chtheme, to cancel .gtk-2.0, to rename .gconf and come back (and in the mean time some settings of .gconf were lost) without success.
Do you have any idea?
I use nvidia proprietary drivers

Thanks
Gianluca

---

### Post by gianluca.pettinello on 2010-06-27
Not a lot of help. Maybe too difficult... for people in this forum?

Anyway I solved by myself. It was libcairo2 last version from xorg-edgers that messed the interface. I had to reinstall everything before finding the solution

Gianluca

---

