---
title: "error update"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by mohdsabri on 2008-12-11
Hi!
During update manager,my pc's hang,
So once restart I try to update again...
but I got this error,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can somebody help me....tq

---

### Post by Michael.Godawski on 2008-12-11
Run the command mentioned in the error message:

```
sudo dpkg --configure -a
```

This usually happens when the installation process was somehow interrupted.

---

### Post by Kevbert on 2008-12-11
It may also be worth running in terminal:
```
sudo apt-get install -f
```
to repair any damaged packages.

---

### Post by JoshuaRL on 2008-12-11
Yep, then a good idea is to make sure everything is updated and cleaned:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

```

---

