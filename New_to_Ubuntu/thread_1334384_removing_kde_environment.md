---
title: "removing kde environment"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-11-22
I recently installed kde (kubuntu) desktop environment and realised that i prefered the original flavor of ubuntu, my question is how would i remove kde using synaptic package manager i have looked but i cant seem to find how to do it 
any input is greatly appreciated, thanks guys

---

### Post by sahabcse on 2009-11-22
If you installed it using aptitude, not apt-get:

#sudo aptitude remove kubuntu-desktop

If you installed it using apt-get:

#sudo apt-get autoremove kde --purge

or

#sudo apt-get autoremove kubuntu-desktop -–purge

---

### Post by Cheesemill on 2009-11-22
You can follow the instructions here [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) to remove all of the KDE packages.

You could do it from Synaptic but the terminal command is alot quicker.

---

### Post by egalvan on 2009-11-22
+1 for psychocat's web site.

Aysiu has some great info on there

---

