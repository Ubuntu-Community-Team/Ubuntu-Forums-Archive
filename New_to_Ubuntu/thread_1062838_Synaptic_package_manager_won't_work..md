---
title: "Synaptic package manager won't work."
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Treelvr on 2009-02-07
Everytime I try to get into this I get an error saying dkpg interrupted use "dpkg --configure -a" to correct problem. But when I do nothing happens. I just get a list of dpkg calls. Any ideras how to fix. Do I need to reinstall synaptic??

---

### Post by billgoldberg on 2009-02-07
> **Treelvr said:**
> Everytime I try to get into this I get an error saying dkpg interrupted use "dpkg --configure -a" to correct problem. But when I do nothing happens. I just get a list of dpkg calls. Any ideras how to fix. Do I need to reinstall synaptic??

Open up a terminal and enter

```
sudo dpkg --configure -a
```

---

### Post by AlexBellisBrown on 2009-02-07
Make sure your up to date also:

sudo apt-get update

---

### Post by Treelvr on 2009-02-07
Thanks, worked. Guess my syntax was off.

---

