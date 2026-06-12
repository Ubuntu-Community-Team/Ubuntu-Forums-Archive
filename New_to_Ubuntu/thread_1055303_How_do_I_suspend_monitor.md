---
title: "How do I suspend monitor?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by hardysummer on 2009-01-30
Is there a command I can use to tell my monitor to go into suspend in a few seconds when I leave the computer?  I do not like turning off the monitor as it makes that static sound on the screen.

---

### Post by kerry_s on 2009-01-30
```
xset dpms force off
```

you can create a launcher or make a shortcut key.

i have mine set on the win key(Super_L)

---

### Post by utnubuuser on 2009-01-30
Ctrl+Alt+L

Check System>>Preferences>>Keyboard Shortcuts  in your top panel

---

### Post by boof1988 on 2009-01-30
> **utnubuuser said:**
> Ctrl+Alt+L

Check System>>Preferences>>Keyboard Shortcuts  in your top panel

Added info...

I need to type in my password after using this.  Is there a way to make it so the screen goes to sleep but a password isn't needed to wake it?

---

### Post by kerry_s on 2009-01-30
look in gconf-editor, use the search function and just uncheck the ask for password on resume.

---

### Post by bruce89 on 2009-01-30
> **kerry_s said:**
> look in gconf-editor, use the search function and just uncheck the ask for password on resume.

That will make no difference, as Ctrl+Alt+L stands for "Lock", which means the session is password protected.

---

