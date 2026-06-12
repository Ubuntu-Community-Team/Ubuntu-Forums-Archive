---
title: "lx panels"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-20
Hi.Does anyone know how I can correct the lxpanels.As you can see in the screenshot,they're or out of line or they "grab" the wallpaper as background.Btw,I don't have this issue with gnome panels.Same for conky.That background shifting doesn't happen in a gnome session.

---

### Post by zvacet on 2010-04-21
If I understand you correctly you don't wont your panels to be transparent.See if right click on panel give you option to set color to panel or under **run command** type **lxpanels** and then try to make color change.

---

### Post by kerry_s on 2010-04-21
right click the panel> panel settings> appearance

interesting wallpaper. :)

---

### Post by dzon65 on 2010-04-21
Hi guys.No,I don't want to colorize or use a background for the panels.I want them transparent.Yet,when I set them to transparency,well,as you can see,they kinda use the wallpaper as background.Same with conky.I don't have this problem with gnome.Only when in a lxde session.Take a look at the more or less same setup in gnome.
Oh btw Kerry,the wallpaper's called isochronous by coolbits.I think I got it from deviantart.(not sure though).

---

### Post by dzon65 on 2010-04-21
Oh almost forgot.Tried to use a custom made transparent gradient jpg as background.Doesn't work,seems it doesn't support transparent jpg or gif or whatever.

---

### Post by dzon65 on 2010-04-21
Turns out that the lxde session starts up ok.But as soon as I log out/in,the panels and conky are messed up.

---

### Post by kerry_s on 2010-04-21
oh, i get it now. you just need to add some time(sleep 3) to the panel & conky so the wallpaper is there first or use the same background for the log in manager so it's already loaded.

---

### Post by dzon65 on 2010-04-23
Ok,thanks.

---

