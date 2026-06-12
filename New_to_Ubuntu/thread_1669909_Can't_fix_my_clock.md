---
title: "Can't fix my clock"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by jermza on 2011-01-18
For no reason, when Ubuntu booted up, an error popped up telling me that the clock couldn't be loaded and then asked me if I wanted to delete it.

I wasn't sure what was happening, so I deleted it (when I probably shouldn't have), as prompted, only to find that it was the actual clock at the top right (and not some funny applet that I might have perhaps installed).

I then right-clicked and saw that I could add the clock to the panel.

However, the clock is now in the wrong place (on the far left).  Without manually moving the icons around (and causing mayhem), is there a way that I can easily restore the icons as they were by default?

---

### Post by cipherboy_loc on 2011-01-18
Thats one of the things that I don't like about GNOME: It screws up your task bars when you use a different resolution and if you have to delete something, and later decide you want it back, it is a pain to get back into place. In other words, no.  I have since switched to Fluxbox, but I occasionally start the GNOME Panels to look at the menu. 


Cipherboy

---

### Post by Frogs Hair on 2011-01-18
Try this.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

