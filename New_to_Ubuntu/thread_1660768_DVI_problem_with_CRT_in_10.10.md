---
title: "DVI problem with CRT in 10.10"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by henry cow on 2011-01-05
I would love to run 2 monitors but I can't quite get there. I have a few years' old Athlon single-core 1.25 and a video card with VGA and DVI outputs, that ran XP for years. I have 2 old but good 17" CRT monitors.

No problems at all when plugging in to the VGA output on the card.

When I plug in to the DVI jack (using a DVI/VGA adapter plug) (in either single or dual monitor configuration) the computer POSTs perfectly, then I get a blank screen with a "Ubuntu" logo with the white/red dots below it for a few seconds.

At that point the screen goes blank and hangs (normally I would see a blinking cursor at top left for a bit, until the main screen comes up).

If I have both monitors plugged in, neither one will come up this way. If I plug in to the DVI jack "hot", it crashes the computer.

Since I get the POST and the very first splash screen, I can only surmise that this is an OS recognition problem rather than a hardware/driver problem.

Can any of you help me with this?

Thanking you so much in advance.

---

### Post by anystupidname1 on 2011-01-05
Can you please post your /var/log/Xorg.0.log and the output from:
```
lshw -C video
xrandr
```

Also, if a /etc/X11/Xorg.conf is present, try renaming/moving it temporarily and trying to boot with the dual monitor setup again.

---

