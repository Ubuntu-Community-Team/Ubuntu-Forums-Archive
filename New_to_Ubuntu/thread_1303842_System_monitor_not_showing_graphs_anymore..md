---
title: "System monitor not showing graphs anymore."
date: 2009-10-28
forum: New to Ubuntu
---

### Post by kajman on 2009-10-28
Some time ago my system monitor in KDE stopped showing graphs (cpu history and network history) and I don't have a clue why.

Anyone experiencing this problem?
Any idea how to solve it? 

I attach a picture of the problem.

---

### Post by kajman on 2009-11-11
If I right-click on the graphs and choose 'properties' then, I can see that my cpu and network traffic sensors are missing (see attachment), but the sensors responsible for RAM and swap are still there, so this graph is plotted.

How can I add those sensors again?

---

### Post by Thalandor on 2009-12-09
I'm seeing the same thing. Reported as [bug #494463]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/494463").

---

### Post by kajman on 2009-12-14
I've solved this problem earlier. You have to delete configuration files for ksysguard somewhere in ~/.kde/

I won't tell you the exact location now, because I've lost my laptop where I had KDE and use xubuntu now (on a veeeery weak stationary PC :P )

---

