---
title: "Crash recovery"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by M1ke on 2010-02-20
I've found that with ctrl, alt & F1 I can log in to a terminal window during a system lockup (i.e unresponsive keyboard, mouse etc so I can't reach my handy force-quit shortcut on the panel to kill the offending app) but my command line knowledge is very limited. Is there a command I can use from there to get back in to my normal GUI? On the few occasions I've needed to, I've simply used it to reboot the system and get back where I was but this particular machine suffers from a long boot time so it's not ideal.

Once I'm in the command line from hitting ctrl, alt & F1 is there a faster way back in to my normal desktop environment than issuing a reboot command?

---

### Post by spiky001 on 2010-02-20
Ctrl+Alt+F7 should do it

---

### Post by Girya on 2010-02-20
once your in a terminal try killing the offending app first:

```
top
```

that will give you a screen with all the running processes 

with top running type k and you will see a line just above the process list that says: 

> PID to kill: with a blinking cursor

then enter the PID number and press enter twice.

then type ctl-alt-F7 to get back to gui

---

### Post by M1ke on 2010-02-21
Brilliant, thank you very much!

---

