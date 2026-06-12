---
title: "Troubles with Compiz"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by setsanto on 2009-02-22
Hi,

I recently tried to upgrade to 8.10, had troubles, and thus downgraded back to 8.04.  Ever since, I've had troubles with compiz.  

I successfully installed compiz 0.7.6, did the multiple backgrounds thing, and turned off Nautilus in order to allow the multiple backgrounds thing to work. It worked fine for the session I was in at that point.  However, when I tried to log in after turning off my computer, I got an error box telling me that the screen wasn't composited and then no desktop elements showed up.  No taskbar, no awn manager, nothing.  All I had was my wallpaper.  Alt+F2 didn't work, but ctrl+alt+F2 did, thank goodness.

What I basically want to know is how can I make nautilus show the desktop from the shell and how can I make compiz start at login?

~Setsanto

---

### Post by stoogiebuncho on 2009-03-01
To turn on Compiz, just enter the command:

```
compiz --replace
```

In order to make it start automatically in the future go to System > Preferences > Appearence > Visual Effects and select "Extra".  

If that doesn't work, take a look at this page:
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz")

---

