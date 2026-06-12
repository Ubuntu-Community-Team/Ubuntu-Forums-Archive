---
title: "no menu at top"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by shaawanoki on 2011-02-10
this is probably a dumb problem, but i just installed 10.10 on my laptop, and i don't have the menu at the top.  the firefox button was the only thing to show up.  i don't know how to get to any options or install any programs.  thanks for any help

---

### Post by Frogs Hair on 2011-02-10
Welcome to the forums

(Desktop edition only)

Right click the top panel > add to panel > add menu bar. To move it right click the icon and select move and place it where you want.

If you are missing every thing but Firefox add the menu then go Applications > Accessories > Terminal. Copy and paste this command and press enter. 

gconftool --recursive-unset /apps/panel && killall gnome-panel

---

