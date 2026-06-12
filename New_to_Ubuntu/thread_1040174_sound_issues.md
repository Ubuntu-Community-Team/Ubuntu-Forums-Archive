---
title: "sound issues"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by koopa225 on 2009-01-15
hey im new here and I have checked a few threads about this but nothing has helped so far. My sound works every now and then, and when it does work and I try to listen to a song I get an error message. Is there a way to fix my sound so I dont have to restart my computer everytime it doesnt work

---

### Post by mc4100 on 2009-01-15
> **koopa225 said:**
> hey im new here and I have checked a few threads about this but nothing has helped so far. My sound works every now and then, and when it does work and I try to listen to a song I get an error message. Is there a way to fix my sound so I dont have to restart my computer every-time it doesn't work

Next time sound stops working, try Alt+F2:
```
killall pulseaudio
```
Restart the application (e.g., Rhythmbox Music Player), and try again. 
If this works, you are suffering from one of the many pulseaudio sound server bugs, which should be fixed when Jaunty is released. 
You might be able to fix it permanently, there are certainly many guides on un-breaking sound, but it could come at the cost of completely braking it altogether. 
If the above works, and doesn't bother you that it needs to be used now and again, I'd just wait around for a update, or for the next release in a few months (which will have a new version).

---

### Post by koopa225 on 2009-01-15
that didnt work either still no sound

---

