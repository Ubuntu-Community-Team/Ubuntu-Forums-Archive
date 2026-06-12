---
title: "Conky Question"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by blueridgedog on 2009-05-06
Is there anyway to exclude conky from being affected by the "hide all windows button"?  It has no window bar, so it is hard to redisplay it, making the show desktop button not useful when running conky.

---

### Post by blueridgedog on 2009-05-06
Disregard...I posted before I searched...

```
own_window_type override
```

---

### Post by spiderbatdad on 2009-05-06
thinking it's the own_window_type override option.
anyway here's the window options on mine...and it is not affected by hiding all windows:
```
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager

```

---

### Post by blueridgedog on 2009-05-06
Thanks....hotpink?

---

### Post by spiderbatdad on 2009-05-06
lol

---

### Post by VCoolio on 2009-05-06
Window type override may have other issues. It's also solvable with compiz.
Uncheck in compiz settings manager > general options > general the option 'hide skip taskbar windows'.

---

