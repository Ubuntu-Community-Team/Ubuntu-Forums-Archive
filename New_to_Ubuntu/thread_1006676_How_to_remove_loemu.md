---
title: "How to remove loemu?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Dirtbead on 2008-12-09
I have installed loemu frontend from the source via the setup.py and would like to know how to remove it. All help is appreciated. I am using ubuntu 8.4 amd64.

---

### Post by Michael.Godawski on 2008-12-09
I would try:
[http://www.experts-exchange.com/Programming/System/Linux/Q_23334949.html](http://www.experts-exchange.com/Programming/System/Linux/Q_23334949.html)

so first 
```
sudo make uninstall 
```
in the src directory of loemu
**[]("http://loemu.pegueroles.com/dists/loemu_0.3.1_i386.deb")**

---

### Post by Dirtbead on 2008-12-09
There is no make file with it just a setup.py which I installed as: python setup.py install.

---

