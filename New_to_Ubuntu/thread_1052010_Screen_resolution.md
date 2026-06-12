---
title: "Screen resolution"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by martrum on 2009-01-27
Hi All,

Absolute beginner - installed Ubuntu yesterday and got it working though !

Trouble is now I seem to be stuck in 800x600 resolution. Same hardware and monitor as previous Windows set up so havn't changed anything.

There seems to be no choices to detect monitor or graphics driver ??

Monitor is an HP1902 - do I somehow search for a driver for it ??

Your help greatly appreciated.

---

### Post by taurus on 2009-01-27
Do you know what kind of graphic does it come with?  Open a terminal and run

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by Lunx on 2009-01-27
> **martrum said:**
> Hi All,

Absolute beginner - installed Ubuntu yesterday and got it working though !

Trouble is now I seem to be stuck in 800x600 resolution. Same hardware and monitor as previous Windows set up so havn't changed anything.

There seems to be no choices to detect monitor or graphics driver ??

Monitor is an HP1902 - do I somehow search for a driver for it ??

Your help greatly appreciated.


I had a bit of a problem when I first installed 8.10 a few weeks ago and being brand new to Ubuntu and Linux I had no idea what to do at first. Then I discovered System > Preferences >Screen Resolution and changed it back to my usual res and problem solved.

---

