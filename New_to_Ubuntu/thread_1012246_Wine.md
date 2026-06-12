---
title: "Wine"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by ibbill on 2008-12-15
I installed wine via the synaptic Package manager.  Just uninstalled via the synaptic manager but it is still listed under  Applications

is there any way I can remove that.

---

### Post by billgoldberg on 2008-12-15
```
sudo apt-get autoremove wine --purge
```

Should do it.

Or just go to "system, preferences, main menu" and remove it from the menu.

---

### Post by ibbill on 2008-12-15
Thanks tried sudo apt-get autoremove wine --purge no luck   so went to the main and unchecked it. Thanks for the quick reply

---

