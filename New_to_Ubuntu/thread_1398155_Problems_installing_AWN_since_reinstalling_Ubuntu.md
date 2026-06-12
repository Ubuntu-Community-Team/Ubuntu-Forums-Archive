---
title: "Problems installing AWN since reinstalling Ubuntu"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-04
I looked in the Awn forums for an answer but couldn't find any. I can't join the forum because I get an error when I try. Since I reinstalled Ubuntu I can't get Awn to work at all. I've uninstalled and reinstlled three times it just won't work. I got this message last  time I tried to start Avant window navigator in terminal

kayte@SuperCow:~$ avant-window-navigator

(awn-applets-migration:2475): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
GConf Error: Type mismatch: Expected `int' got `float' for key /apps/avant-window-navigator/bar/bar_angle
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop

Thanks for any help :)

---

### Post by J V on 2010-02-04
run this and see if theres a change:

```
gconftool-2 --type int --set  /apps/avant-window-navigator/bar/bar_angle 45
```

---

### Post by ThePinkWitch on 2010-02-04
> **J V said:**
> run this and see if theres a change:

```
gconftool-2 --type int --set  /apps/avant-window-navigator/bar/bar_angle 45
```

Thankyou so much, it's working. The only thing is that I have completely different Awn Manager (The Menu thing) to the one I had before and it has less options. I can't select to stretch the toolbar right across the bottom like in the last one and there are fewer icons and nowhere to adjust the size of them that I can see. I'm wondering If I have installed an older version or something. Anyway Thanks for your help :)

---

