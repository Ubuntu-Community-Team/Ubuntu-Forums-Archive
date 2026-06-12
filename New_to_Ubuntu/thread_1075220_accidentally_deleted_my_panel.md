---
title: "accidentally deleted my panel"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by deleyd on 2009-02-20
I accidentally deleted my panel (at the top of the screen.) I added a button for the System Monitor, but clicked "Add" twice, and tried to delete the extra one, and ended up deleting the entire panel instead.

Oops. How do I get it back/make a new one?

(How do I get to System Monitor anyway?)

---

### Post by northern lights on 2009-02-20
Hit Alt+F2, type```
gnome-panel
```and hit Enter. Voila.

---

### Post by Liviu-Theodor on 2009-02-20
You could access System Monitor also with the command ```
gnome-system-monitor
``` given in a terminal or a Run Application windows (Alt+F2).

---

### Post by deleyd on 2009-02-20
> **northern lights said:**
> Hit Alt+F2, type```
gnome-panel
```and hit Enter. Voila.
Tried that. No response. I was able to create a *blank* panel by right-clicking on the lower panel at the bottom of the screen and selecting "New Panel". But it's blank. I'm not sure what things I'm supposed to add to it to make it right again.

---

### Post by deleyd on 2009-02-20
I found a solution
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

ALT-F2
gnome-terminal
[gets the terminal line mode window. Enter these 3 commands:]
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by northern lights on 2009-02-20
Oh, okay. You still have the panel application running, but just deleted one panel. Shucks.

Here's what you do after creating a new one on the top:

Right-click the new panel and add: "Menu Bar", "Clock", "Notification Area" and "User Switcher". Move the newly added applets to where they were or you want them. You should thus be able to recreate the original panel as it was after installation.

[EDIT]
Starting with a fresh configuration obviously works as well. Sorted, then.
[/EDIT]

---

