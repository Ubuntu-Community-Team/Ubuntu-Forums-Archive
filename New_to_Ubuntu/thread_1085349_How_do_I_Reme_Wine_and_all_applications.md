---
title: "How do I Reme Wine and all applications"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-02
Hi,
My wine installation is screwed.
When I try to uninstall itunes and other things I've installed, most say they encountered an error when trying to remove.

So I was wondering how I remove wine and all it's apps manually?

Thanks

---

### Post by oldos2er on 2009-03-03
Open a terminal, and run
```
rm -rf .wine
```

---

### Post by Gp. on 2009-03-03
Hi,
I did this, and wine is still under applications and the apps are still appearing in the menu.

---

### Post by bodhi.zazen on 2009-03-03
that command removed your wine installation.

To remove wine from the system

```
sudo apt-get remove --purge wine
```

---

