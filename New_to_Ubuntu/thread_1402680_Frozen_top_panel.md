---
title: "Frozen top panel"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by mikemykel on 2010-02-09
A couple of days ago I was experimenting with my panels and all seemed to be going well but now my upper panel is completely frozen.  i.e totally non-responsive.  I can get to Firefox by going through a site I had placed on the desktop.  

Does anyone have any suggestions?  If so please remember that I am very new to Linux.  I am also an old man and not very bright so please talk slow and simple.  Thanks, Mike

---

### Post by unmole on 2010-02-09
This will restore the default gnome-panel

Hit Alt+F2 and type
```
 sudo debconf gnome-panel 
``` And run it in terminal.
Hope that fixes it.

---

### Post by moacir.souza on 2010-11-12
Hum... If you just want to restart everything, you could use a simple:

```
sudo killall -s HUP gnome-panel
```

---

