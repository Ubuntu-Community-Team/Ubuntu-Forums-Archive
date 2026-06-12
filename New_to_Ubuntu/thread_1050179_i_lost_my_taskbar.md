---
title: "i lost my taskbar"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-01-25
i removed it by accident. is there a way to get it back?

---

### Post by eragon100 on 2009-01-25
> **infernus_crusher said:**
> i removed it by accident. is there a way to get it back?

You lost just one of the two? Right click on the other one and click on "new panel." :wink:

Then to get all of the icons etc. that where on it back, right-click on the newly formed panel and select "add to panel."
Then, just select all of the things that where on it before deletion and click-and-drag them back to the right place.

---

### Post by Michael.Godawski on 2009-01-25
hi, see here:

[http://ubunturesources.ub.ohost.de/gnomepanel.html](http://ubunturesources.ub.ohost.de/gnomepanel.html)

---

### Post by llamabr on 2009-01-25
Which one is the taskbar, the one at the top, or the one at the bottom?

In either case, right click on the other one, and choose 'new panel', then follow the instructions.

---

### Post by sisco311 on 2009-01-25
To restore the default panels rename the ~/.gconf/apps/panel directory, press Alt+F2 and run:
```
killall gnome-panel
```

then press Alt+F2 and run:
```
gnome-panel
```if needed.

---

### Post by UbuntuNerd on 2009-01-25
if you want your panels to their default settings like they were before just type this commands in a terminal:```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Phospholipid on 2009-03-23
I have done exactly the same thing, but gnome-panel command stuff seems to have absolutely no effect on my system. 

I then looked and found no file in ~.gconf/apps/ marked with panel in the name. 

However then my computer froze (again!). I'm looking at re-ienstallation I think.

---

