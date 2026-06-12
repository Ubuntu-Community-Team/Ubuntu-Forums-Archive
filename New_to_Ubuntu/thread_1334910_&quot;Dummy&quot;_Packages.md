---
title: "&quot;Dummy&quot; Packages"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-11-22
I just installed Chromium BSU from Synaptic with the package *chromium*. This is listed as a "Transitional (Dummy) Package" and I was curious as to what a dummy package is and whether or not they should be removed after installation or if they are like metapackages?

---

### Post by mgranet on 2009-11-23
Dummy packages are packages which are used when the name of a package has changed. If you had a package named programA, and you wished later to rename it programB, you would link the old package to the new, so that anyone trying to install the package by the old name(programA) would get the proper package. It is safe to delete, just like a metapackage.

---

### Post by Martin Marshalek on 2009-11-23
Okay, cool the game is great by the way!

---

