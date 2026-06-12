---
title: "Ahh!! Infinite amount of System Monitors on Panel. Cannot remove/ Resource Hog"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Lauxmonster on 2010-03-21
Hello,

I am having a great deal of trouble here and I do not know if it is common or not, but here's how it goes.

I turned on my computer today and found that my entire panel was filled with System Monitors. You may say, "right click, remove" but no, this does nothing to solve the problem. When I delete one, another comes and takes its place. Right now, I am running at about 75% CPU utilization just on running the System Monitors. I do not know what happened. It seems like a bug.

A restart fails to fix the problem. I am contemplating a fresh Ubuntu install. Does anyone know what to do? It is really interfering plus the fact that they mess up the entire look.

Here's what it looks like. Blue = CPU utilization.....Black = unused...very little black.

[IMG]http://i288.photobucket.com/albums/ll183/Theaxethrow/wtfsystemmonitors.png

How do I get rid of this. And on startup?

Thanks

---

### Post by skatinjj on 2010-03-21
You could try booting into failsafe Gnome and take a look at your startup programs to see if there is anything messed up.

---

### Post by Elfy on 2010-03-21
You could also revert to the default panels 

```
gconftool &#8211;recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Lauxmonster on 2010-03-21
> **forestpiskie said:**
> You could also revert to the default panels 

```
gconftool –recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

Thank you. I originally thought it did not work but it required a restart. You ubuntu guys/girls are so knowledgeable about commands and problem fixes. I would never understand how to put two and two together like that.

Problem solved.

---

