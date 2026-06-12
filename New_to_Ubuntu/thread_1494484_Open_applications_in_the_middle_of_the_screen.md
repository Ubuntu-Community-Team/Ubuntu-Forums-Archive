---
title: "Open applications in the middle of the screen"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by tij on 2010-05-27
Any suggestions on specifying where an application is positioned on the screen when it is opened?  For example, I'd like to have a new  terminal window positioned in the center of the screen when opened.

---

### Post by shai3421 on 2010-05-27
You could move to kubuntu, since KDE has better options for this sort of thing.

See this:
[http://brainstorm.ubuntu.com/idea/1442/](http://brainstorm.ubuntu.com/idea/1442/)

---

### Post by aninaiian on 2010-05-27
You can do this in Ubuntu if you have compiz (visual effects) running.  I think the easiest way to do so is to install ccsm (CompizConfig Settings Manager) via
```
sudo apt-get install compizconfig-settings-manager
```

Open up ccsm in the menu via Applications -> System -> Preferences -> CompizConfig Settings Manager or by typing
```
ccsm
```
in a terminal.  Under the "Window Management" heading there should be "Place Windows" make sure it's checked and click it to configure that plugins settings.  Go to the tab called "Fixed Window Placement," and click new under the "Windows with fixed placement mode."  Then set Windows to "name=gnome-terminal" (no quotes) and set Mode to "Centered."

---

