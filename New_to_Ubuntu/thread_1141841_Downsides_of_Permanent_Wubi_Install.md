---
title: "Downsides of Permanent Wubi Install?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by TAllen013 on 2009-04-28
Are there any downsides of using a Wubi install as my permanent dual boot configuration as opposed to partitioning the disks?

---

### Post by MontelEdwards on 2009-04-28
Well one of the things is that it really is going to run a lot slower in Wubi then if Ubuntu had the whole computer to its self rather than sharing with Windows. In Wubi, Ubuntu is run from within Windows. Your Ubuntu install is dependent on your Windows install. If you lose your windows OS, to malware or something like that, you also lose your Ubuntu install.

---

### Post by drs305 on 2009-04-28
If you haven't installed wubi yet and plan on making it permanent, make sure you provide ample space. A common post on these forums involves requests asking how to make the wubi 'partition' larger. Since it isn't a partition but simply a file inside Windows, this isn't simply done. There are workarounds, but in general you can 'resize' a wubi install as you can a normal install.

I believe the default size is 8GB but you should do a search for recommendations.

---

