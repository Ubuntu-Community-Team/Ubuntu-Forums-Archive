---
title: "Use emerald instead of compiz"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by cartisdm on 2010-01-16
I was reading through an issue of Linux Format (btw, awesome magazine), and they introduced me to the fantastic looking window boarder effects when running Emerald.  I have been running Compiz with all the effects, I have the Emerald Theme Manager installed, and when I open a terminal and type
```

emerald --replace

```

All the window boarders change to exactly how I want them and still save all the compiz settings.  Problem is, soon as I close the terminal the settings all revert.  How do I enable Emerald permanently?

---

### Post by Linuxforall on 2010-01-16
Install compiz-fusion icon, run it and select Emerald theme manager and it will stick even when you reboot.

---

### Post by nothingspecial on 2010-01-16
Or just put emerald --replace in system > preferences > startup applications.

To keep emerald after closing the terminal run emerald --replace after pressing Alt-F2

---

### Post by nick_goodfate on 2010-01-16
or go system->preferences->compizconfig settings manager , click on window borders to see its options and in the field "command" replace whatever it has by default with "emerald --replace"

---

### Post by cartisdm on 2010-01-16
Thanks guys!!!! Now my desktop is looking fantastic! :)

---

