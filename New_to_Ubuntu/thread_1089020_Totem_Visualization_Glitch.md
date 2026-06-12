---
title: "Totem Visualization Glitch"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-03-06
Totem has been weird since i upgraded to Ibex, the visualization is still visible, even when the window isn't on top. it's not solidly on top, it flickers over the current window unless i minimize totem to the taskbar.

basically, when it's not minimized, i can see it no matter what window is open.

i managed to catch two screenshots (tapping Print Screen FTW!)
[IMG]http://dl.getdropbox.com/u/285667/Pictures/Movie%20Player%20Glitch/Movie%20Player%20Glitch.png[/IMG]

[IMG]http://dl.getdropbox.com/u/285667/Pictures/Movie%20Player%20Glitch/Movie%20Player%20Glitch%202.png[/IMG]

I'm using Totem with Xine
```
Totem Movie Player 2.24.3
Movie Player using xine-lib version 1.1.15
```

how can i fix this? it's really annoying

---

### Post by Toxicity999 on 2009-03-07
Sounds like a video driver bug. You should give some more information on your graphics hardware. That aside... Why do you have the visualizer activated when you aren't looking at it? If you're alt tabing away the majority of the time, why even waste the cycles?

---

### Post by Yashiro on 2009-03-08
Ati video card?

---

### Post by Sonic Reducer on 2009-03-08
> **Yashiro said:**
> Ati video card?

```
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
```

---

### Post by Yashiro on 2009-03-09
It's a driver overlay+totem bug. More common with the latest round of drivers as they try to make various things work while compiz is active.

---

### Post by Yashiro on 2009-04-03
This bug is fixed in (ati fglrx) Catalyst 9.3.

---

