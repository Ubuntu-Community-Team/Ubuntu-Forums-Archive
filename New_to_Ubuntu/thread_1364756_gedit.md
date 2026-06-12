---
title: "gedit"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by dzon65 on 2009-12-26
Sometimes when using gedit,it freezes part of the system (menus,some open windows)and cpu is skyrocketing.No idea what's causing this.Added a screenshot where you can see what happens.It takes a few secs for that menu to load (now it's just a window,no text),the gedit window turns gray,can't drag it nothing.This takes about a minute to turn to normal.

---

### Post by fancypiper on 2009-12-26
Do you see any error messages if you launch gedit from a terminal?

---

### Post by dzon65 on 2009-12-26
When entering gksudo gedit I get this:yui@ubuntu:~$ gksudo gedit
/home/yui/.themes/Kuler 2 v3/gtk-2.0/gtkrc:34: Kan invoegbestand ‘styles/panelstyles’ niet vinden
/home/yui/.themes/Kuler 2 v3/gtk-2.0/gtkrc:624: error: invalid string constant "panel", expected valid string constant
yui@ubuntu:~$ 
This refers to the gtk theme I've got installed but I don't see how this could be giving this (sometimes) weird behaviour.

---

### Post by dzon65 on 2009-12-26
BTW,this is nice :"Not a window in the house but somehow there's more light..."

---

### Post by fancypiper on 2009-12-26
How did you install the theme? I recommend installing as much software as you can with Synaptic.  I seem to have fewer problems that way.

Have you tried removing and re-installing the theme

---

### Post by dzon65 on 2009-12-26
The theme is pretty clean.The "error" referred to in the terminal is just because I removed a part from the theme's gtkrc.And,this only happens once and a while.But still,when it happens,the cpu goes really up,even starting the fan.Since I installed ubuntu,memory never went up 40%,never even heard this fan.It's not life-threatening but still,annoying.

---

