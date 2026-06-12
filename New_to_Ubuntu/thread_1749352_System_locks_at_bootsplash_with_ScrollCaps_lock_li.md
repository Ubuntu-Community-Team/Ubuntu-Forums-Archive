---
title: "System locks at bootsplash with Scroll/Caps lock lights blinking on keyboard"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-04
Well this is a new one for me.  Don't know what to make out of it.  All I can say is I didn't apply any updates before going to bed last night and when I started Ubuntu today, the very instant the bootsplash screen appears the system seems to halt, and the caps lock and scroll lock lights on the keyboard start blinking.  I have to force it down to get out of the snag.

Any idea what these blinking lights mean?

---

### Post by diablo75 on 2011-05-04
Just solved this on my own.

I had remembered that, for some strange reason, this Line6 Studio GX (it's a USB guitar pre-amp/external sound card) causes a kernel panic.  This never happened with 10.10.  Unplugging it before boot gets around the problem, but it's not a solution.

Probably should do some googling and see if there's a bug report about this somewhere.

---

