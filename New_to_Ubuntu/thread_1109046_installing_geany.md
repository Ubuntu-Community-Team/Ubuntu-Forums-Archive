---
title: "installing geany"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-28
I am wondering how to install geany on ubuntu 8.10.  I have downloaded the program and i have it on my desktop.

---

### Post by argie on 2009-03-28
Your best bet is to install from the software repository.

1. Go to System > Administration > Synaptic Package Manager
2. Search for geany (or) Select the Development section on the left and scroll down.
3. Mark geany to install by selecting the checkbox next to it.
4. Agree to mark all the dependencies that are mentioned in the box that pops up.
5. Click Apply.

or

```
sudo aptitude install geany
```

If you find version in the repository too old for your use, you can download the [Geany .deb from getdeb]("http://www.getdeb.net/app/Geany") and double-click it to install. It is usually better to use the repository version, however.

---

