---
title: "Lost Panel Icons 10.4"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by zeke1312 on 2011-05-04
Hi, New to Ubuntu. I've searched for this ? but found none specific. I "played around" w/Ubuntu and managed to lose the icons located at the top left side of the panel (Applications,etc). How do I restore? Thank you

---

### Post by ~Plue on 2011-05-04
Right click the panel > add to panel > menu bar
Or if you want to completely reset the panels to the default, press alt+F2 and run
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```

---

