---
title: "Deleted my panel!"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Automag05 on 2010-07-13
I am very  new to Ubuntu and I accidentally deleted my top panel!!!!! I've been surfing how to restore it, and found the command

"gconifgtool-2--shutdown"
rm-rf~/.gconf/apps/panel
pkill gnome-panel

Except when every I type in "gconifgtool-2--shutdown" the terminal says the command is not found. I really want my panel back to its default state... again, I am very new and having some GUI is a help :)
I am running version 10.04, all advice is appreciated!

Thanks!

---

### Post by sisco311 on 2010-07-13
To restore the default panels, run:
```
gconftool --recursive-unset /apps/panel
```
```
killall gnome-panel
```
If the panles do not restart automatically then, run:
```
gnome-panel &> /dev/null &
disown
```

---

### Post by mbzn on 2010-07-13
Right click on the bottom panel, select 'new panel'. Move that to the top and right click that, now select add to panel. See through all the features and keep the ones you like... move them to where you want and (right click > select lock to panel) until everything is the way you need it.

Good luck.

---

### Post by Automag05 on 2010-07-13
Thank you guys... I have my original panel again :) that's a relief.

---

