---
title: "A quick question about installin apps"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by cygnis1 on 2009-10-27
Which is better?  Using add/remove, synaptic, or apt-get?  Which one will give you the latest apps?  I am using Jaunty.
Thanks,
Cygnis1

---

### Post by fancypiper on 2009-10-27
It's your choice and all of them should get the latest apps.  I use synaptic unless I want to add just a few, then I use apt-get.

---

### Post by gnuisancev3 on 2009-10-27
> **cygnis1 said:**
> Which is better?  Using add/remove, synaptic, or apt-get?  Which one will give you the latest apps?  I am using Jaunty.
Thanks,
Cygnis1

All of these are getting apps from the same exact place. 

If you look at the file /etc/apt/sources.list  or any of  the files in /etc/apt/sources.list.d/

The lines in these files list what repositories the software is pulled down from. 

Add/remove is simply the most user friendly method. Syaptic gives you a bit more control via a GUI than Add/Remove.  Apt is command line and has many many options and is generally much faster to use.

---

### Post by philinux on 2009-10-27
> **cygnis1 said:**
> Which is better?  Using add/remove, synaptic, or apt-get?  Which one will give you the latest apps?  I am using Jaunty.
Thanks,
Cygnis1

They all got the latest versions, however, add/remove only contains a subset of the whats in synaptic. It's meant as an easy way of installing popular apps for new converts.

Synaptic and apt-get is really the same thing.

---

### Post by cygnis1 on 2009-10-27
Thanks, All.

---

