---
title: "Graphics Issues with Linux Install"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Tomas49 on 2008-12-19
Trying to install Linux for the first time, am absolutely not familiar with pretty much anything related to it.  Got through the install process, but after restarting the computer like it prompts you to do, I get nothing but a black screen.  Reinstall Ubuntu using the safe graphics mode, works, except for the fact that now the screen can only be described as too big for the monitor.  Hoping someone can tell me how to fix this, as the only screen resolution available is 800x600.

---

### Post by Malalo on 2008-12-19
Could you post your hardware details please ?
Also I'm guessing (since I had a similar problem) that you should try to activate the restricted graphic drivers. You can do so by going in
System -> Administration -> Hardware Drivers
You'll find a restricted driver for your graphical adapter which you can activate or deactivate.

---

### Post by Tomas49 on 2008-12-19
Unfortunately, when I go to hardware drivers nothing shows up

---

### Post by weezerisrock on 2008-12-19
Do you happen to know what video card your system has?

---

### Post by Tomas49 on 2008-12-19
Unfortunately I don't, as this is my first time with linux I used an old system that my parents had stopped using, and am unfamiliar with the specs on the system (I do know it has 1/2 a gig of ram in it).

---

### Post by BrandonBan6 on 2008-12-19
> **Tomas49 said:**
> Unfortunately I don't, as this is my first time with linux I used an old system that my parents had stopped using, and am unfamiliar with the specs on the system (I do know it has 1/2 a gig of ram in it).

Tomas, can you post the model number of the machine?

---

### Post by Tomas49 on 2008-12-19
Dell Dimension 2350, thanks for the help everyone

---

### Post by scorchgeek on 2008-12-19
I would suggest booting into recovery mode and selecting "Try to fix X config". Have you tried that?

---

### Post by BrandonBan6 on 2008-12-19
Tomas,

Here is a similiar post I found:
[http://ubuntuforums.org/showthread.php?t=281035](http://ubuntuforums.org/showthread.php?t=281035)

I would try Scorchgeek's recommendation first, but if not, I'd see you could edit the xorg.conf file. Do you get a boot option menu?

---

### Post by Tomas49 on 2008-12-19
When I go to xfix, it gives me a line about overwriting possibly customized configuration

---

### Post by scorchgeek on 2008-12-19
Don't worry about it. Just continue. It will make a backup anyway, and plus you can't have a customized configuration yet, having just installed.

---

