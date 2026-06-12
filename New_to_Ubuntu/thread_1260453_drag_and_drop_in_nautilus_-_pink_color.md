---
title: "drag and drop in nautilus - pink color"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by seattle vic on 2009-09-07
Whenever I move files via a drag & drop using nautilus, a pink coloring  slowly scrolls from top to bottom before you can drop.

I read somewhere that it's related to compiz, but I removed that and no change.  I then found there's a bug report, but nothing on when it will be fixed.

Anybody know if this is still a bug and what could be done to fix it?

I'm using 9.04 64 bit ubuntu.

---

### Post by keplerspeed on 2009-09-07
Just check that compiz is not enabled, right click on your desktop and go to change desktop background>visual effects and set to none. See if the issue persists.

Do you have an intel graphics card? To see what it is enter this to the terminal:
```

lspci | grep VGA

```

---

