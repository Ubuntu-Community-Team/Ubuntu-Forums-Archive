---
title: "Accidentally deleted the Panels"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by daoster on 2010-11-07
Hey all, I seem to have done something to the panels on Ubuntu...I've accidentally deleted the default ones (Where I go access my programs, or configure my settings, or the Places menu...)

Anybody know how to add it back?

---

### Post by t.rei on 2010-11-07
Easy - I use this everytime I mess things up beyond reason:

In a terminal type:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill  gnome-panel
```

if alt+f2 still works: run gnome-terminal
if this doesnt work: strg+alt+f2 will take you to a textbased login. Should work there as well. strg+alt+f7 or f8 takes you back to the graphics.

---

### Post by daoster on 2010-11-07
Thank you very much!

---

