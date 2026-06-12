---
title: "msttcorefonts"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by aszxcv on 2010-07-20
i just upgrade to 10.04 from 8.04 not from cd but from terminal. i had msttcorefonts install on 8.04 but now 10.04 it isn't install on my system. I cant find it in 10.04 synaptic package manager. Are there any alternative packages i can download so i can get the fonts i want?

> msttcorefonts:

Package msttcorefonts has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by Paqman on 2010-07-20
Go to System > Admin > Software sources, and make sure all the repos you need are enabled (presumably you want "restricted")

Ubuntu disables all except the core repos during upgrades, to make sure that non-official software doesn't mess up the upgrade. Once you've got the new system installed, it's ok to go back and re-enable the rest.

---

### Post by aszxcv on 2010-07-20
i am still not getting it.  where do i click once i do Go to System > Admin > Software sources?


ubuntu software?
other software?
updates?
authentication?
statistics?

---

### Post by oldos2er on 2010-07-20
In 10.04, the package name is ttf-mscorefonts-installer, in the multiverse repository.

---

### Post by aszxcv on 2010-07-20
thank you both 


i  got it :D

---

