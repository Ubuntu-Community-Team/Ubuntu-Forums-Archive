---
title: "installing kde4 in interpid"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by pardesi on 2009-02-12
How do i install kde4(completely and nt only the core) in my interpid?

---

### Post by xebian on 2009-02-12
> **pardesi said:**
> How do i install kde4(completely and nt only the core) in my interpid?

Kubuntu.org is your friend

---

### Post by Ptero-4 on 2009-02-12
install the kde-environment (or something like that) and you´ll get the full thing.

---

### Post by mc4100 on 2009-02-12
> **Ptero-4 said:**
> install the kde-environment (or something like that) and you´ll get the full thing.
Presuming the KDE version in Intrepid is KDE4 (anyone running Kubuntu Intrepid know?):
```
sudo apt-get install kubuntu-desktop
```

---

### Post by Ptero-4 on 2009-02-12
> **mc4100 said:**
> Presuming the KDE version in Intrepid is KDE4 (anyone running Kubuntu Intrepid know?):
```
sudo apt-get install kubuntu-desktop
```
That command installs all the kubuntu custom stuff, which the OP may not have intended to install. kde-environment gives him KDE 4.2 with the vanilla configuration (the same one that kde-core gives) but with more programs than the ones in kde-core (kde-core is kdebase and a few other apps, kde-environment is kde-core plus kdemultimedia, kdepim, kdenetwork, kdeadmin, kdeaddons, kdegames, etc).

---

### Post by xeth_delta on 2009-02-13
You can follow the instructions from this page: [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)
Just be carefull, as usual when installing something additional.

---

