---
title: "aptitude or apt-get"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by A_M_S on 2009-06-09
hi.

Is there any advantage in  apt-get over aptitude?


The aptitude saves the packages dependencies which can save a lot of work when uninstalling some aplications (kde for example).



Thanks

---

### Post by aysiu on 2009-06-09
apt-get also now saves the dependencies.

Just do ```
sudo apt-get autoremove
``` to remove the applications.

The only real advice I would give you is that you stick with one or the other. Don't mix and match using *aptitude* and *apt-get*.

---

### Post by A_M_S on 2009-06-09
> **aysiu said:**
> apt-get also now saves the dependencies.

Just do ```
sudo apt-get autoremove
``` to remove the applications.

The only real advice I would give you is that you stick with one or the other. Don't mix and match using *aptitude* and *apt-get*.

but apt-get don't save dependencies in large applications like KDE, right?

---

### Post by jenkinbr on 2009-06-09
It should.  Apt (and Apt-get) is desktop-environment independent.  If an app requires dependancies, apt will note them.  If you remove something later on, apt may suggest you remove some packages that were needed before as dependancies, but are no longer needed because the dependant package(s) are no longer installed.

---

### Post by A_M_S on 2009-06-09
When i removed KDE with apt-get was necessary do list all the packages.

---

### Post by jenkinbr on 2009-06-09
When you removed KDE, how did you remove it?  If you just removed KDE, you will still have KDE installed due to the fact that the kde package is a metapackage.

If you want to remove all of kde, try ```
sudo apt-get remove kdelibs5
```

Be advised: this package is a dependancy of almost all KDE apps. removing it should cause anything KDE to be removed.

Be sure to scan the list of packages apt-get or aptitude wants to remove - sometimes it will do something stupid and want to remove essential packages.

Also note that some packages that depend on kdelibs5 are packages you may want to keep.  I.E. - I run gnome, but I like Amarok for my music.  Amarok depends on kdelibs5, and so removeing kdelibs5 will also remove amarok.

---

### Post by A_M_S on 2009-06-09
Thanks for the tips :)

But with aptitude the metapackage dependencies are saved, right ?

---

### Post by aysiu on 2009-06-09
> **A_M_S said:**
> Thanks for the tips :)

But with aptitude the metapackage dependencies are saved, right ?
And, as some of us have also explained, in *apt-get* they are saved as well. That is what *apt-get autoremove* is for, to remove the no-longer-needed dependencies.

---

### Post by A_M_S on 2009-06-09
> **aysiu said:**
> And, as some of us have also explained, in *apt-get* they are saved as well. That is what *apt-get autoremove* is for, to remove the no-longer-needed dependencies.

The apt-get autoremove didn't work for me with the metapakage kde :(.

I had to remove the packages manualy

---

