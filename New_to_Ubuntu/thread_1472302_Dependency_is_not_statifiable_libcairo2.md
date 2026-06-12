---
title: "Dependency is not statifiable: libcairo2"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Existance0 on 2010-05-04
I'm trying to install the mysql workbench but I downloaded the deb and tried to install it but it it says "Error: Dependency is not satisfiable: libcairo2".

So, I went to terminal to install it...
```
sudo apt-get install libcairo2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcairo2 is already the newest version.
```

So... somethings not right here?

---

### Post by tica vun on 2010-05-04
The versions probably don't match, seeing as how you're trying to install an application that's not in the repositories.

---

### Post by Drenriza on 2010-05-04
try
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```
 
to satisfy dependencyes.

---

### Post by Existance0 on 2010-05-04
It only upgraded java.

---

### Post by Existance0 on 2010-05-04
This is probably because I'm still running 8.04 thus I'm updating Ubuntu. I'll bump this thread if upgrading to 10.04 doesn't fix it.

---

