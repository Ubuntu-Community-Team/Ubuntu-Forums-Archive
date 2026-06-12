---
title: "omg, how do i fix this?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by ptviperz on 2009-03-03
I was playing around with the blue space theme and transparency and suddenly all of my menus are invisible. Obviously can't get back into the manager and fix it. 

Think the application panel and right click menus are now invisible. Thank God I still have my awn dock but I need to fix this. Please someone tell me how to change back to the default theme. Should I uninstall the compizconfigmanager?

---

### Post by albandy on 2009-03-03
open a console, if press alt+f2 and type gnome-terminal
now type
gnome-appearance-properties

and edit your settings

---

### Post by nothingspecial on 2009-03-03
If you are using emerald and compiz try pressing Alt+F2 and typing

```
metacity --replace
```

---

### Post by ptviperz on 2009-03-03
> **nothingspecial said:**
> If you are using emerald and compiz try pressing Alt+F2 and typing

```
metacity --replace
```

awesome, that worked. I can fix it from here....

---

### Post by ptviperz on 2009-03-03
> **albandy said:**
> open a console, if press alt+f2 and type gnome-terminal
now type
gnome-appearance-properties

and edit your settings

That gave me this

brent@desktop:~$ gnome-appearance-properties 
/home/brent/.themes/BlueSpace/gtk-2.0/gtkrc:375: Unable to locate image file in pixmap_path: "Combo/combo-pressed.png"
/home/brent/.themes/BlueSpace/gtk-2.0/gtkrc:378: Background image options specified without filename
/home/brent/.themes/BlueSpace/gtk-2.0/gtkrc:375: Unable to locate image file in pixmap_path: "Combo/combo-pressed.png"
/home/brent/.themes/BlueSpace/gtk-2.0/gtkrc:378: Background image options specified without filename

** (gnome-appearance-properties:6376): WARNING **: Invalid borders specified for theme pixmap:
        /home/brent/.themes/BlueSpace/gtk-2.0/Scrollbars/trough-scrollbar-vert.png,
borders don't fit within the image

(gnome-appearance-properties:6377): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
/home/brent/.themes/BlueSpace/gtk-2.0/gtkrc:375: Unable to locate image file in pixmap_path: "Combo/combo-pressed.png"
/home/brent/.themes/BlueSpace/gtk-2.0/gtkrc:378: Background image options specified without filename


For future reference, where would I go from there?

---

