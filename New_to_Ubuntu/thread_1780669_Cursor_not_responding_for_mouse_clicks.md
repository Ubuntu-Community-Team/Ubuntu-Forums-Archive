---
title: "Cursor not responding for mouse clicks"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by PraveenP on 2011-06-12
Hi, Some times in Unity Mouseclicks not working on bottom half of the application (mainly in browser)! No such problem found yet  in GNOME. Wonder why? Please help

---

### Post by Rocket2DMn on 2011-06-12
There have been a lot of reports about this, and I experience this sometimes as well. The problem is apparently caused by an invisible window which blocks the mouse.

[https://bugs.launchpad.net/unity/+bug/709461](https://bugs.launchpad.net/unity/+bug/709461)

Apparently running
```
compiz --replace
```
or even
```
unity --replace
```
works, though I haven't had a chance to test it out yet.

---

