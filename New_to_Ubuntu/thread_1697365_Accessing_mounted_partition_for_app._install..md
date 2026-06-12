---
title: "Accessing mounted partition for app. install."
date: 2011-02-28
forum: New to Ubuntu
---

### Post by rajesh_joshi on 2011-02-28
Hi,

I installed Ubuntu on a laptop with limited space on the root partition. I have since then, added/mounted another partition. How do I make Synaptic install non-essential apps etc on this new partition? 

RJ.

---

### Post by seawolf167 on 2011-02-28
The applications you install will be placed where the developer decided to place them. The binaries are usually placed in one of the locations defined by your default PATH variable, i.e.

```
echo $PATH
```

things like config files are usually placed in /etc

So, in short, unless you compile each package from source with commands to place the built files elsewhere, you can't install them outside the / file structure.

The easiest solution is to simply resize your / partition to give you more space for future-installed packages

---

