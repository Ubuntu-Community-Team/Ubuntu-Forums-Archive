---
title: "How to identify hardware for acquiring drivers in *gasp* windows?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by nintennuendo on 2009-01-21
So I'm at work, my last week, and we're a small museum, so we take what we can get.  We have an anonymous computer with hardware we can't identify in windows, and short of taking the whole thing apart, can't find the drivers.  However, when booting from the ubuntu live cd, it picks everything up just fine.  Is there a way to find the name of all the hardware?

tl;dr how to find out wat hardware is installed?

---

### Post by abyssius on 2009-01-21
You can begin by opening a terminal (System->Accessories->Terminal) and typing:
```

lspci -v

```

---

### Post by hyper_ch on 2009-01-21
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by stalkingwolf on 2009-01-21
or install Gnome device Manager.  It is in Synaptic.

---

