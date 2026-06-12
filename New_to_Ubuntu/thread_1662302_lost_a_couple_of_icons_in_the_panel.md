---
title: "lost a couple of icons in the panel"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by tweedmeister on 2011-01-07
I lost a couple of objects or icons in the panel. Instead of having the wireless connection icon, I have a black square. I right clicked and went to the "add to panel" window, but now the wireless connection icon is not even listed among the items to move into the panel. I hoped rebooting would help, but it doesn't. Didn't I originally get the wireless connection icon (the antenna symbol with signal strength bars) from the "add to panel" list.? if not, where is it found? If you do get it from the list, and it's no longer there, how do you get it back?
thanks.

m

---

### Post by LADmaticCA on 2011-01-07
I would first try opening a terminal (Applications>Accesories>Termnial)and running:

```
killall gnome-panel
```

This will restart the gnome-panel sometimes fixing load errors.


If that does not work try right-clicking the panel and select "Add to panel" and select Notification Area. If that does not work you may have to add Indicator Applet from the same menu.

---

