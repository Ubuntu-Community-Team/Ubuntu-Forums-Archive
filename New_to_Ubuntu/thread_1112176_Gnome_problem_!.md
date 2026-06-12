---
title: "Gnome problem ?!"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by alket on 2009-03-31
I installed
sudo apt-get install kubuntu-desktop

i restarted lap top and I noticed that gnome is running but with some kde packages,
i tried to remove kubuntu-desktop
sudo apt-get purge kubuntu-desktop
but the files are still here and i cant use some gnome packages.

How can i remove kubuntu-desktop permanently ?

---

### Post by alket on 2009-03-31
please help !!!

---

### Post by James_Lochhead on 2009-03-31
Like this:

```

sudo apt-get remove kubuntu-desktop
sudo apt-get autoremove

```

---

### Post by James_Lochhead on 2009-03-31
The autoremove command removes packages that are no longer needed because the package that needed them is gone.

---

### Post by Tibuda on 2009-03-31
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

