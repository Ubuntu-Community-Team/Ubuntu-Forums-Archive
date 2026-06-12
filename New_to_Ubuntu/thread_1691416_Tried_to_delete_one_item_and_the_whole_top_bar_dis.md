---
title: "Tried to delete one item and the whole top bar disappeared"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by jimgd on 2011-02-19
Hi --

I managed to delete everything at the top of the screen when trying to remove a single panel. So Applications Places Etc are all gone. 
Help!

Thanks

---

### Post by yeats on 2011-02-19
Try this in a terminal:

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

It will reset your panels to default settings.

---

### Post by Hakunka-Matata on 2011-02-19
since you have no way to access "Applications > Accessories > Terminal" use ALT-F2, click on the down arrow at the right hand side of the empty area where your blinking cursor is, then select gnome-terminal, run .............

---

### Post by jimgd on 2011-02-19
The combined solutions resurrected the bar at the top after I restarted.

Thanks much

---

