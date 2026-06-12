---
title: "weird problem, aaplication menu frozen!"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by mahmater on 2009-02-12
when I started yesterday updating my intrepid ibex, the application menu froze. and it still does.I restarted the system so many times and I also deleted the menu bar from the panel and added it again but in vain. now,i can't access the application menu.

can you help please?

---

### Post by pastalavista on 2009-02-12
you could try opening a terminal and running
```
sudo apt-get update
```
and then
```
sudo aptitude safe-upgrade
```
and if that doesn't work,
```
sudo apt-get install gnome-desktop
```

... or at least, that's probably what I would do before searching for a fix or asking for help myself, possibly won't help, but I don't think it could hurt

---

### Post by mahmater on 2009-02-14
thanx friend. I tried ur suggestion but still couldn't open the application menu. it's really strange.

---

