---
title: "aMule loading error"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by PepeLapiu on 2009-12-28
I can't get aMule to load properly. Here is the terminal stuff:
> pepelapiu@pepelapiu-laptop:~$ amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
No other instances are running.
ListenSocket: Ok.
HTTP download thread started
Loading temp files from /home/pepelapiu/.aMule/Temp.

All PartFiles Loaded.
Host: amule.sourceforge.net:80
URL: [http://amule.sourceforge.net/lastversion](http://amule.sourceforge.net/lastversion)
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (amule:1967): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

What's the problem?
What's that mean?
How can I correct this?

Thanx all for your great help.

Cheers,
PepeLapiu :)

---

### Post by Hallvor on 2009-12-28
Surprise.. well, not really.

[https://bugs.launchpad.net/ubuntu/+bug/183969](https://bugs.launchpad.net/ubuntu/+bug/183969)

xserver-xorg-core breaks wxwidgets in aMule. Looks like aMule is out of action until someone fixes the bug.

---

