---
title: "Windows on multiple desktops"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Jonnythm on 2011-03-15
I'm pretty new with ubuntu/linux in general (been running it for a few months now) and am wondering if there is a way to make windows not overlap onto multiple desktops.

What I mean by that is, when you have visual effects enabled if a window is off to the side of one desktop so that a part is not on the desktop, the part that is not on the current desktop is visible on the desktop next to it, and when you switch to that desktop you can see it. I know that this is not the case on low graphics which suggests that it's possible to turn off that feature. 

I looked through the Compiz Config Settings Manager (CCSM) and couldn't find a way to do it through that, but I could have overlooked something.

Thank you for your input.

---

### Post by /usr/bin/hacked? on 2011-03-16
I don't think this is possible because of the way that compiz treats the desktop as one long, wrapped, viewport. You can try something like maxumize (which makes a window go as big as it can without overlapping other windows), and that may work for you.

---

### Post by Jonnythm on 2011-03-16
Hmmm, ok I suspected that might be the case. Something I noticed was I stretched out a window so it went around the entire desktop cube, and on the screen where it started, it didn't actually appear twice. Instead it acted as if part of it didn't exist.

The attached screen shot is the view of it in the 3d cube.

---

### Post by grahammechanical on 2011-03-16
Have you tried in CompizConfig Settings Manager the snapping windows plugin. Under the behavior tab there are two check boxes: Screen edges and window edges. I have both ticked and I cannot do what you are doing. Each desktop on my machine acts as a separate desktop. I think that this is what you want.

Regards.

---

