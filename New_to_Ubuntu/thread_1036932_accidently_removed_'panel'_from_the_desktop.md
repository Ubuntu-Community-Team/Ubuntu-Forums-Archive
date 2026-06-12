---
title: "accidently removed 'panel' from the desktop"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by spyo on 2009-01-11
I just got Kubuntu, and I accidently removed the entire panel from the desktop.  Is there a certain chain of keys I can press to get it back?

---

### Post by RomeReactor on 2009-01-11
Hi. Which version of Kubuntu are you running?

Please open a Konsole and try this, one command at a time:
```
kquitapp plasma
```
```
rm ~/.kde/share/config/plasma-appletsrc
```
```
plasma
```

---

### Post by snova on 2009-01-11
Unlock widgets, right click on the desktop, and press Add Panel.

You'll have to put the menu, taskbar, and systray back on manually.

No need to restart Plasma, it's already running...

---

