---
title: "Black Screen"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by TAllen013 on 2009-04-09
I've got Wubi installed on Win XP.  I tried to change the screen resolution and as soon as I did the entire screen went black.  Is there any way that I can reset the system to its default values while still at the boot menu?  I can't do anything actually inside Ubuntu because absolutely nothing is visible (the boot menu is still visible, it turns all black right after the log-on screen)?

---

### Post by fabricator4 on 2009-04-09
Yes, press and hold the <ctrl> and <Alt> keys while pressing the + key on the numerical keypad.  The screen should rotate through available resolutions each time time you press '+' until you find one that works.

Chris

---

### Post by billgoldberg on 2009-04-09
If this worked, please add [SOLVED] to the title of the thread.

---

### Post by Jakey_TheSnake on 2009-04-09
If it doesn't, try booting into recovery mode, then entering: 

```
sudo dpkg-reconfigure xserver-xorg
```

into a terminal.

---

