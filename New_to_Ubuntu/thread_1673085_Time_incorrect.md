---
title: "Time incorrect"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by olemathgeek on 2011-01-21
I triple-boot my MacBook and the time stamp in OSX is correct.  However,  when I boot into Ubuntu (Lucid) the time is 6 hours off.  If I change  the time to the correct time, then when I log back into OSX the time  stamp there is off.  Does anyone know how to correct this error while  avoiding changing the time every time?

---

### Post by jroa on 2011-01-21
I just set my time in Linux to GMT +0 to bandade the problem.

---

### Post by srs5694 on 2011-01-22
To fix the problem, you need to tell Linux that the system clock stores time in UTC rather than in local time. This is easy during installation (there's a check-box for it on the time setting page). I'm not sure offhand how to do this from a GUI after Ubuntu is installed, but there may be an obvious and easy way to do it. (I'd check, but my Ubuntu desktop system is shut down right now). One reference I found suggests that you can do it by editing the /etc/default/rcS file and changing the following line:

```

UTC=no

```

...to read:

```

UTC=yes

```

That reference is five years old, though, so it's possible the relevant configuration file has changed.

---

