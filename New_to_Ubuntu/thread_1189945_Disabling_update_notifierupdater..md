---
title: "Disabling update notifier/updater."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-06-17
Anyone know how to disable the update notifier LIke what command do you use to stop it.

I am making a live cd, and it gets annoying seein gthis pop up at the top right hand corner.

---

### Post by newbee70 on 2009-06-17
Have you gone into: system/Administration/software sources/update? and set your preferences?

---

### Post by ericeclifford on 2009-06-17
I need to do it in a chroot environment through command line.

---

### Post by zvacet on 2009-06-17
If you don't want to get any updates then in your source list add # sign in front of every line.Save and close file.

```
sudo apt-get update
```

---

### Post by ericeclifford on 2009-06-17
> **zvacet said:**
> If you don't want to get any updates then in your source list add # sign in front of every line.Save and close file.

```
sudo apt-get update
```

Ok so I got it now, so when  I remove my source lists in my live cd customization do a apt-get update and it should not have a pop up baloon saying there are updates/upgrades ready to be install correct?

---

### Post by alienkid10 on 2009-06-17
and you won't be able to install anything.

---

### Post by ericeclifford on 2009-06-17
its ok, its going to be a live cd, cant save anything.

---

