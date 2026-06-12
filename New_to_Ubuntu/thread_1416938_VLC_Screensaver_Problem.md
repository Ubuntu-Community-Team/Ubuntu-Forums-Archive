---
title: "VLC Screensaver Problem"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by infestor on 2010-02-26
i use vlc 1.0.2 and apparently ubuntu (karmic) doesnt regard it as an active process or whatever so after sometime my screensaver is in effect. 
is there a solution for this irritating problem?

---

### Post by Ozymandias_117 on 2010-02-26
Unfortunately, no. It is due to a change in how Ubuntu deals with interrupts (it now uses a different engine to handle them, I believe it has something to do with HAL being depreciated) VLC still does it the old way, so it doesn't work. You will have to use another media player like xine. I believe Kaffine also works.

---

### Post by infestor on 2010-02-26
gnome screen saver is disgusting btw

---

### Post by -memetic- on 2010-02-26
> **infestor said:**
> gnome screen saver is disgusting btw

haha

---

