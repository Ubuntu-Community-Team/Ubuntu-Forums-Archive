---
title: "Theme Managers, and Window Decorators..."
date: 2009-02-28
forum: New to Ubuntu
---

### Post by sMash! on 2009-02-28
Need a little help here. Just got Compiz up and running, and went ahead and installed Emerald while I was at it. I'm using one emerald theme as a tester (Gaia08 Linux). Now, I can get the gaia08.emerald to work, but I have to use the terminal and 'replace' my currently in-use window decorator (which is?...im a n00b) but as soon as I close that terminal, I lose my window decorations entirely (no window bar at the top). Only way I get it back is a restart.....I've tried doing --replace with "gtk-window-decorator" and of course "emerald" but same thing; as soon as I close the terminal, *poof*. Did I miss something somewhere, and there's a way to switch these things outside of the terminal?


Please advise the ignorant on how to use different theme engines, managers, and window decorators properly? KTHX.

---

### Post by N4zgu1 on 2009-02-28
> **sMash! said:**
> Need a little help here. Just got Compiz up and running, and went ahead and installed Emerald while I was at it. I'm using one emerald theme as a tester (Gaia08 Linux). Now, I can get the gaia08.emerald to work, but I have to use the terminal and 'replace' my currently in-use window decorator (which is?...im a n00b) but as soon as I close that terminal, I lose my window decorations entirely (no window bar at the top). Only way I get it back is a restart.....I've tried doing --replace with "gtk-window-decorator" and of course "emerald" but same thing; as soon as I close the terminal, *poof*. Did I miss something somewhere, and there's a way to switch these things outside of the terminal?


Please advise the ignorant on how to use different theme engines, managers, and window decorators properly? KTHX.

You can use "alt f2" for running "emerald --replace" instead of using the terminal.

For returning to the default decorator you can run

```
metacity --replace
```


P.D. If you want to run emerald every time you start you can go to preferences > sessions > Add > command an there you type emerald --replace

---

### Post by Ms_Angel_D on 2009-02-28
Actually I would suggest going to add/remove programs and installing compiz fusion icon You can use it to select your theme manager and window decorator.

---

### Post by sMash! on 2009-03-01
Thanks MHA, that should do nicely. One teeny step further from n00b-ness!
:popcorn:

---

### Post by Ms_Angel_D on 2009-03-01
No problem glad to be of assistance :D

---

