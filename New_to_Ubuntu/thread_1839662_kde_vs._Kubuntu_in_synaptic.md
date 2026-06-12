---
title: "kde vs. Kubuntu in synaptic"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by Shmook on 2011-09-06
Hello, so for about 4 years I've been going on and off with Ubuntu while checking out other distros as well. It remains my favorite, thought a fondness for Puppy has also arrived.

Anyway, I've install 11.4 Xubuntu, as xfce is my DE of choice, but I occasionally like to play with others, and I was looking in synaptic to install LXDE and/or KDE, and I saw there's separate entries that confused me, for example you can install:

"lxde" OR "lubuntu desktop"
or
"kde-plasma-desktop" OR "Kubuntu-desktop"

I'm wondering if there's a difference between these two entries. Is it just that the Kubuntu-desktop includes more apps and such than the kde-destop? Or are they different names for the same thing? Thanks

---

### Post by 3rdalbum on 2011-09-06
> **Shmook said:**
> 
"lxde" OR "lubuntu desktop"
or
"kde-plasma-desktop" OR "Kubuntu-desktop"

I'm wondering if there's a difference between these two entries. Is it just that the Kubuntu-desktop includes more apps and such than the kde-destop? Or are they different names for the same thing? Thanks

Look at the list of dependencies (right-click the package and choose Properties, then in the second tab you can look at the dependencies). You'll see that lxde just installs the LXDE environment, and "lubuntu" installs Lubuntu's whole defaut program set - so it'll install everything that comes on the CD, assuming you don't already have it.

---

### Post by snip3r8 on 2011-09-06
I got the kde desktop running on natty with kde-plasma-desktop

---

### Post by NightwishFan on 2011-09-06
**kde-plasma-desktop** is the name of the kde package in Debian. It was pulled in from Debian but likely should work correctly on Ubuntu. **kubuntu-desktop** is the package that installs the full Kubuntu desktop session. They are both what are called 'metapackages' which are simply packages that contain a small bit of information and depend on a lot of other packages. They can also safely be removed.

kubuntu-desktop probably includes much more software as kde-plasma-desktop only includes kde software as far as I know.

---

