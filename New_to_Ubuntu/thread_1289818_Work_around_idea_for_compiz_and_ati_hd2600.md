---
title: "Work around idea for compiz and ati hd2600"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by brophus on 2009-10-12
Ubuntu going to sleep on a laptop with ati hd2600 graphics card works flawlessy...unless the compiz effects are enabled. It crashes before the log in screen. With multiple color ubuntu lagged across the top of the screen. I have tried multiple work arounds and supposed fixes but the issue still exists. So now with a fresh install im wondering if anyone could or has done what im about to propose. What if before the computer goes to sleep compiz is shutdown and when it resumes compiz is enabled after log in. I dont know how to go about this or if someone has done it before, but any help is greatly welcomed. Thank you in advance

---

### Post by gali98 on 2009-10-13
Hmmm... It sounds like it could work. As for going about doing it,
there are two directories you need.
/etc/apm/suspend.d
and 
/etc/apm/resume.d

These directories use scripts similar to /etc/init.d/.

As for the commands, 
compiz --replace will replace metacity(default window manager) with compiz.
As for the other way around, metacity will have a similar command, though I don't know it.
Kory

---

