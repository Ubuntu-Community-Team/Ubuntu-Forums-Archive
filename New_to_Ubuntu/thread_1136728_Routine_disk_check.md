---
title: "Routine disk check"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by triangleSLO on 2009-04-25
I am just wondering where do I find results of routine disk check that pops up every 30 mounts?

---

### Post by Sidewinder1 on 2009-04-25
Never thought about it but try this in the terminal:
```
man fschk
```You might find the location of results in there.
That being said, I think it's a "No news is good news" situation and that if there's a problem, you'll see it on screen right after fschk finishes.
HTH
 Side


OOps, sorry about that! 
Thanx forestpixie...
A thousand pardons..

---

### Post by Elfy on 2009-04-25
```
man fsck
```

Logs are in /var/log/fsck

---

