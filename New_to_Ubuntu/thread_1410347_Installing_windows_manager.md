---
title: "Installing windows manager"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-02-18
Hello all,
    I've got a fresh install of ubuntu 9.10 server and I'd like to set it up so I can launch graphical programs when I need them, but be in command line the rest of the time, no desktop. Something like install kde and then compiz? Would that accomplish what I want?

---

### Post by DrMelon on 2010-02-18
An interesting approach would be something like "ion3" - which looks like a terminal most of the time, but you can launch graphical apps.

---

### Post by woodsonoversoul on 2010-02-18
Thanks, I'll look into it. I'd really like to play with KDE though, just not sure exactly how to set it all up...

---

### Post by lykwydchykyn on 2010-02-18
If you want something familiar yet lightweight, I'll recommend LXDE.

The commands would be:
```

sudo aptitude install xorg lxde

```

---

### Post by lykwydchykyn on 2010-02-18
> **woodsonoversoul said:**
> Thanks, I'll look into it. I'd really like to play with KDE though, just not sure exactly how to set it all up...

If you want the whole Kubuntu desktop, the package to install is kubuntu-desktop.

If you just want kde, the packages to install would be either kde-minimal, kde-standard, or kde-full.  kde-full is a lot of extra stuff, but to be honest I've found that kde-minimal and even kde-standard seem to be missing some important things (like the tray mixer, kmix, for example).

Any of those plus xorg will get you what you need.

---

### Post by nothingspecial on 2010-02-18
server + kde is an interesting choice.

```
sudo apt-get install kde-minimal
```

---

### Post by woodsonoversoul on 2010-02-18
Would something crazy like kde-minimal + compiz work or be more trouble than it's worth? Of course I want it to be fast, stable, and look amazing with no compromises ;)

---

### Post by lykwydchykyn on 2010-02-18
If you've never used KDE before, you're probably best off just running kwin.  Why complicate things with compiz?  Kwin also has compositing and effects, but unlike compiz it's integrated into the desktop environment and can interact with plasma.

---

