---
title: "Problem in booting Ubuntu 8.10"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by kapmsd on 2009-02-04
I have Ubuntu 8.10 Interpid Ibex.
Many items during booting,it is not starting with my monitor signalling "No signal".
After ubuntu progress bar screen this happens.
So every time, i need to reboot, wishing it won't happen next time.
Please help me reg this.

---

### Post by Omegaxis on 2009-02-04
I am having a similar [issue.]("http://ubuntuforums.org/showthread.php?t=1036357")

You can stop by my thread and see if anything suggested will help.

When it says no signal, try pressing CTRL+ALT+F1. and see if that brings up a terminal screen.

---

### Post by kapmsd on 2009-02-04
Thanks.
Oh k.I ll try it out.
What may be the reason for such problem?
This is totally irritating.

---

### Post by Omegaxis on 2009-02-04
Technical answer: your monitor probably doesn't specify a resolution and refresh rate in the EDID.

Easy answer: When your graphics card asks your monitor what resolution and refresh rate it runs at, your monitor replies with "I can run whatever resolution and refresh rate you want!" to which the graphics card replies "No I asked you first" and then they fight about it.

This is more likely to happen with an LCD monitor.

It could also be _very many_ other things. I've just seen that one a lot.

---

