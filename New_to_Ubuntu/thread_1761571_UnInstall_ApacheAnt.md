---
title: "UnInstall ApacheAnt"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by myselfmani on 2011-05-18
How to UnInstall Apache Ant on Ubuntu?

---

### Post by wishyjr on 2011-05-18
Hiya,

How was the package installed? you could use:

```
apt-cache search (package name)
``` to find the package and then:

```
apt-get remove (package name)
``` to remove it.

Alternatively, synaptic could be used to search and remove if you're running a GUI.

---

