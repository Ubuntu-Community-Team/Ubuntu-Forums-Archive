---
title: "Panel Empty!!!"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Nathan Cunningham on 2010-06-13
I was messing around with settings and things, REALLY long story short.... I can no longer tell what is being used on my desktop on the panel. I have to use alt+tab to select anything. Or have everything [SIZE="1"]really[/SIZE] small so that I can select between different windows. Any help? Btw, I am using 9.04

---

### Post by llawwehttam on 2010-06-13
right click on the panel > add to panel > window list > add.

Should solve the problem.

---

### Post by Rodemire on 2010-06-13
Yep, i second the above, just add the windows switcher to your panel. Unfortunately all windows are grouped here so you have to go through the list when you wish to change to another window.
Or, alternatively, you could use a window manager like AWM or Cairo-dock, better eyecandy.

---

### Post by tom.swartz07 on 2010-06-13
If you really borked it up, you could always remove the preferences for the panels by opening a terminal and typing

```
sudo rm -rf ~/.gconf/apps/panel
```

Note that this will undo any and all changes that you have made to the panel, and will be fixed upon the next time you log-in

---

