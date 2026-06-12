---
title: "close, minimize,expand put on the right hand side like  windows"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by ap892008 on 2010-11-16
how do you put the close on the right hand side of the window that is open

---

### Post by Verbeck on 2010-11-16
open *gconf-editor* (alt+F2 to bring up the run dialogue)
navigate to /apps/metacity/general
change the value for button_layout to [I]menu:minimize,maximize,close
[/I]
menu = a small dot/arrow that shows the window menu
: = separates left and right side by the title

edit: alternatively, you could use a theme which keeps the window controls at the right side

---

### Post by drs305 on 2010-11-16
Here's a quick way:
```

gconftool-2 --set --type string /apps/metacity/general/button_layout ":minimize,maximize,close"

```

You can move the min,max,close words around to suit your preferences. The colon at the start or end determines the side.

---

### Post by jotto! on 2010-11-17
Or if your using the latest version, a one click answer can be found by using ubuntu tweak

Applications > System Tools > Ubutnu Tweak

Scroll down to Desktop and click on Window Manager Settings, first Item IIRC.

---

