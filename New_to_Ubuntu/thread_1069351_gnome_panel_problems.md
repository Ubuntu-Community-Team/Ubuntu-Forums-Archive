---
title: "gnome panel problems"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by cygnis1 on 2009-02-13
I am having problems with my gnome panel. the bottom panel.  It started out with the icons being moved to the oposite side of the panel.  Then any opened applications weren't showing up in the panel.  Now I have no icons in the bottom panel.  How do I restore my bottom panel?
Thanks,
Cygnis1

---

### Post by RomeReactor on 2009-02-13
Hi. From a terminal (Applications->Accessories->Terminal):
```
gconftool-2 --shutdown
```
Then:
```
rm -rf ~/.gconf/apps/panel
```
And lastly:
```
pkill gnome-panel
```

---

### Post by cygnis1 on 2009-02-13
Thanks,  
That seems to have worked.  Now my network icon is gone from the top panel.

---

### Post by RomeReactor on 2009-02-14
The Network Manager applet should have shown up after you restored the panels. In any case, when people say the NM applet isn't showing, most of the times is the Notification Area applet that's missing. You can right-click on an empty space in the top panel, select "Add to Panel...", and double click on the Notification Area applet. That should bring the NM applet back.

---

