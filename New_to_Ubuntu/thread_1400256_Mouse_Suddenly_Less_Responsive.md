---
title: "Mouse Suddenly Less Responsive"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Sparty26 on 2010-02-06
Hello, I am having a problem. I installed 9.10 on a Sony Vaio PCG-K33. It was an old computer, possibly from 2003 (it belonged to my brother, it was running slow, over heating, so, BAM! Ubuntu saved the day!). At first, everything worked fine, but suddenly, today when I started it up, the mouse was extremely slow. Now, it appears that the areas around the touchpad edges work best for trying to move the mouse and the area in the middle of the touchpad is almost completely non-responsive. I fear it may be a hardware issue, but I figured I would see if anyone else had the same problem? Any help is appreciated, thank you!

---

### Post by blazemore on 2010-02-08
Try a totally different system, such as a Fedora liveCD, or Windows.
If you still have the same problem, it's almost certainly hardware.

---

### Post by SaikoRonin on 2010-02-20
Ive tracked down the source of the problem, 

I'm getting an error on bootup 

"Connect-Debounce Failed, Port 7 Disabled"

Seems as if this may be a common bug,  and may not be related to Lucid Lynx,  but it sure is odd that it only started affecting me since updating the dist.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88530]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88530")

---

