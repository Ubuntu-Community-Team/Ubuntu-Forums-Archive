---
title: "automatic program startup preventing successful login"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by rockerphil on 2009-04-23
ok, the title is pretty self explanatory, but here's a quick rundown. i shut down Xubuntu without first closing out all my running programs (xmms Pidgin and Firefox) and since my system resources are pretty limited every time i try to log in to the only account on the system it tries to load all those running programs upon startup, overloads itself and kicks me back to GDM so if anyone has a way i can disable this particular feature i'd be greatly appreciative, and please remember, i can't log in graphically so please keep it either terminal based, or if there's a way i can do it from one of my other Linux installs by editing a config file or something to that effect it'd be greatly appreciated. much thanks in advance,

Phil

---

### Post by LowSky on 2009-04-23
at GDM, boot into safe mode, then log out, then boot into normal mode

---

### Post by rockerphil on 2009-04-23
do you mean Failsafe Gnome? cus if so my machine doesn't have the resources to run Gnome

---

### Post by decoherence on 2009-04-23
I don't know from XFCE, but these things are likely kept in a config file that you can edit. Tell GDM to log in to a failsafe xterm, cd in to your ~/.config directory and see if there's anything that looks promising. 

This document might help you figure it out. Particularly, check the Advanced section.

[http://www.xfce.org/documentation/4.2/manuals/xfce4-session](http://www.xfce.org/documentation/4.2/manuals/xfce4-session)

good luck,

---

### Post by LowSky on 2009-04-23
> **rockerphil said:**
> do you mean Failsafe Gnome? cus if so my machine doesn't have the resources to run Gnome

whoops you using XFCE, I need to read better.

ok other suggestion

boot into recovery mode, choose boot to terminal option, log in then type startx

---

### Post by Sir Jasper on 2009-04-23
Hi,

I can only suggest you have a look at your settings:

Settings>Settings Manager>2nd Icon [Button Label Sessions and start up].

My regards

---

### Post by kanikilu on 2009-04-23
I haven't tried this yet myself (pretty new to XFCE), so instead of removing, to be on the safe side, just move the sessions cache folder: ```
mv ~/.cache/sessions ~/.cache/sessions-backup
```

---

