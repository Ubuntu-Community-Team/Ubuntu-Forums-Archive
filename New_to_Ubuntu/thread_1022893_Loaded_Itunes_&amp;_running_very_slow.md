---
title: "Loaded Itunes &amp; running very slow"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by JACKSPERRO on 2008-12-27
Hi everone,
Loaded itunes through Wine and itunes is running painfully slow (about 3 minutes between keystrokes or mouse actions) any help greatly appreciated.
thanks.
Jack

---

### Post by itix on 2008-12-29
What do you need iTunes for?

I know perfectly well that iTunes runs horribly through wine. My brother needs iTunes since apple has gone stupid and closed their protocols for transfer between computer and iPhone/iPod touch. If you however have something older than any of theese two, I'd strongly reccomend Banshee which is a strong candidate for replacing iTunes in functionality.

---

### Post by RichardLinx on 2008-12-29
If your running the latest version of iTunes then It's very likely to run horribly on any Linux machine, apple isn't a very big fan of Linux. If you need iTunes that badly then you can try running an older version through wine. You're much better off following itix's advice and installing banshee. 

Run in terminal:

```
sudo apt-get install banshee
```

I use banshee myself and works beautifully. For more information visit:[http://banshee-project.org/](http://banshee-project.org/)

---

### Post by itix on 2008-12-29
Yeah... Apple has really gone stupid in recent years. Closing protocols, selling f*ing updates, raising the price of their products like mad etc. They are digging their own grave.

One who swallows a to large bite risk choking upon it.

---

### Post by Master Chief on 2008-12-30
> **JACKSPERRO said:**
> Loaded itunes through Wine and itunes is running painfully slow (about 3 minutes between keystrokes or mouse actions) any help greatly appreciated.

What hardware (CPU/memory/etc) do you have?  Running Ubuntu 32 or 64 bit?  Which Ubuntu version are you using? 

Note: iTunes works very well in VirtualBox (without CoverFlow support for iTunes) and VMWare Player with CoverFlow support (I like VMWare Workstation myself, because it supports more CPU cores and thus my application, like iTunes run faster/smoother).

---

