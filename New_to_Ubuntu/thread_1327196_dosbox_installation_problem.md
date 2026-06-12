---
title: "dosbox installation problem"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by rumca.js on 2009-11-15
I cannot install dosbox. I tried also to install freedoom, but same message popped out. It happened after installation of scilab or before installation of dosbox. Should I download any of this packages that dosbox depends on?


user@user-laptop:~$ sudo apt-get install dosbox
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dosbox: Depends: libsdl-net1.2 but it is not going to be installed
          Depends: libsdl-sound1.2 (>= 1.0.1) but it is not going to be installed
  fop: Depends: libxerces2-java but it is not going to be installed
  libxalan2-java: Depends: libxerces2-java (>= 2.8.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Paqman on 2009-11-15
Have you updated your package lists?

---

### Post by rumca.js on 2009-11-15
Ok. I rebooted, filtered in synaptic sources packages, reinstalled broken packages, I tried to install packages from commandline, rebooted again....   and somehow I managed to install dosbox, scilab and freedoom.
However I am unable to play freedoom because after a few seconds it goes back to desktop :/   I will probably search the forum for similar problems.

---

