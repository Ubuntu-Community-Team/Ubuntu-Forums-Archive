---
title: "Mouse in non-existent area using extended desktop"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Argaen on 2010-10-04
I'm using Ubuntu 10.04, my notebook resolution is 1366*768 and my external monitor is at 1280*1024. They are configured side by side, with the external monitor on the right side, keeping the top of both desktops aligned.
The issue I'm having is that my mouse can get to the unused area below my laptop screen, where it can't be seen.
I have attached an screenshot, where the bottom left black area is outside my visible desktop and where the mouse pointer can get (you can see it there).
Can this be fixed without changing the resolution or position of the screens?

---

### Post by Crazedpsyc on 2010-10-04
I have no such problem with the exact same specs. No idea why this is but attach a screenshot of your System>Preferences>Monitors program opened. This configuration program should automatically detect the differences in resolution and it should work. If reconfiguring from this program doesn't work the only thing I can think of is making a program that overlays on the screen and prevents the cursor from moving past a certain point, but that should be very last resort

---

### Post by Argaen on 2010-10-04
I have attached here my monitor preferences (one screenshot for my laptop screen and one for the external monitor).

One thing I forgot to mention was that my monitor native resolution was not autodetected, so I added it by hand using:```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
```

My laptop is a Samsung R430.

---

### Post by Argaen on 2010-10-05
I haven't been able to resolve this issue, but noticed another bug. The icons in the desktop can get to the invisible area (as seen in attached screenshot). 
I can select and use them as normal, but it has to be from memory only, the only way I found to see them is using rotate cube from compiz.
It took me time to notice this because I usually do not have more than 4 or 5 things in my desktop.

---

