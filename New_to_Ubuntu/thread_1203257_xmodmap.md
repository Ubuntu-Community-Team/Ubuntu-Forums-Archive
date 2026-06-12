---
title: "xmodmap"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by csevolution on 2009-07-03
How do I make xmodmap remap button 9 on my mouse to button 8? Or 9 to 10 for that matter?

---

### Post by Aearenda on 2009-07-03
This will reverse buttons 8 and 9:
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 9 8"
```
You just list the desired outcome in the order they occur really. But you do have to account for every button, it seems - you can't name a button twice.

---

### Post by csevolution on 2009-07-03
Yeah I figured it out after reading the manual.

How do I make that get executed whenever a user logs into GNOME?

---

### Post by kpkeerthi on 2009-07-03
Systemm -> Preferences -> Startup Applications -> Command

---

### Post by csevolution on 2009-07-03
/etc/X11/Xmodmap is a better place.

---

### Post by csevolution on 2009-07-03
Thanks anyhow.

---

