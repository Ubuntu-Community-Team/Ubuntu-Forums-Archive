---
title: "Cannot access desktop after making changes to desktop effects"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by judhampson on 2009-03-08
Hi all,

I have made a change to the desktop effects setting in KDE 4.1 and now can't see anything except blackness when I login.

I am currently trying to fix via the command line as I can't get past the login screen if logging on normally.

Other details:

Kubuntu is installed as a dual boot via Wubi on a Windows XP laptop. No dedicated partition has been set up.

Regards

Jud

---

### Post by ibuclaw on 2009-03-08
If this is compiz, it's probably best to reset those settings back to their defaults.

In the console terminal:
```
rm ~/.compiz -r
```
Or, to remove and restore the defaults on **ALL KDE Settings** you've made
```
rm ~/.kde -r
```

That is if you are willing to loose all customisation you have done to your desktop.

If you wait around a while, someone who works with KDE4 may be able to pinpoint exactly what to do with resetting everything.

Regards
Iain

---

