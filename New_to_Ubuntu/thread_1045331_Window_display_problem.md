---
title: "Window display problem"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by melrokz on 2009-01-20
1. When i restart my pc, when i open windows in Ubuntu 8.10, they only cover half the screen. I'ts not a window resizing problem. I'll have to run 'monitor resolution settings' to correct the display. Why?

2. Why is openoffice 3 missing from the repos?

---

### Post by gettinoriginal on 2009-01-20
Go to System, Administration, Software Sources and add this to your Third Party Repos.
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
Then in terminal run:
```
sudo apt-get update
```
Then you should find OO3 in Synaptic.  :p

---

### Post by gettinoriginal on 2009-01-20
Sorry, forgot to address the window problem:
If you are running compiz, copy/paste in the terminal:
```
compiz --replace
```
If you are running metacity:
```
metacity --replace
```

---

### Post by Tatty on 2009-01-21
> **melrokz said:**
> Why is openoffice 3 missing from the repos?

Each stable release of ubuntu is "locked" in the repos, and only security or stability (or minor) bugfixes are allowed.  This is to limit the ability for new bugs to creep in.

If you want to install open office 3 then you will need to install it from another source.
The official site offers a .deb which might work.  [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

