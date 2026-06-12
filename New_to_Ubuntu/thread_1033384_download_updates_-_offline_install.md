---
title: "download updates - offline install"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by bhouncy on 2009-01-07
Is there anywhere I can download the latest updates for 8.10 so I can put them on a flash drive to transfer to another computer that has no internet?

---

### Post by northern lights on 2009-01-07
Use *aptitude download* instead of *apt-get install* or *aptitude install*.

From a prompt within /home, it can be run without root rights, like so```
aptitude download PACKAGENAME
```where PACKAGENAME obviously needs to be replaced by an existent package.

Further check [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and [http://www.getdeb.net]("http://www.getdeb.net").

---

### Post by bhouncy on 2009-01-07
Thankyou. Much appreciated.

---

