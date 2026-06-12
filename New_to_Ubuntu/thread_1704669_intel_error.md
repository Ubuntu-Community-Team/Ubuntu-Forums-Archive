---
title: "intel error"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by go2xraj on 2011-03-11
ebox-printers : Depends: foomatic-db but it is not going to be installed
E: Broken packages

This is the error coming in installing intel graphics, please help me

---

### Post by Krytarik on 2011-03-11
I guess you will get those error when trying to install *any* package. To fix the issue, try these commands:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```
If these go well, run these thereafter:
```
sudo apt-get update
sudo apt-get upgrade
```
Then you might install what you want.

---

