---
title: "Flash player 10"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by r5gtt2k3 on 2009-02-20
It doesn't seem to be working properly for me, Some things don't work on my machine, How do i go back to using a previous version of flash player ? Also some sites are not displaying properly, I'm not sure if it has something to do with flash player, I think it happened after i last updated (using 8.10)

---

### Post by RomeReactor on 2009-02-20
Hi. How did you install Flash--from the repositories, or from Adobe's site? Is you Ubuntu system 32 bit, or 64?

---

### Post by sandyd on 2009-02-20
he got it from the repositories.

---

### Post by RomeReactor on 2009-02-20
> **carlee said:**
> he got it from the repositories.

It will also be useful to know how many entries for **Shockwave Flash** there are in Firefox:
```
about:plugins
```

And how many libflashplayer.so instances there are on the system:
```
sudo updatedb; locate libflashplayer.so
```

---

