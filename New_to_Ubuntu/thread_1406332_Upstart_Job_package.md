---
title: "Upstart Job package?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Julita on 2010-02-13
Hi! I am unable to install Network Manager because of the dependency with the package "upstart job." The problem is that there is no such package (at least it is referred to as a virtual package, but the one that I have - upstart - obviously is ignored.) Any help would be much appreciated.

---

### Post by NightwishFan on 2010-02-13
Hi, perhaps you could tell me what version of Ubuntu you have, and the output of the command:
```
sudo apt-get -f install
```

If the command ask you to remove more than 1 or 2 packages, do not hit yes when prompted.

---

### Post by Julita on 2010-02-14
Hi! Thanks for your help. The output was really weird because the program wanted to remove several packages - upstart, related libraries and... usplash, at the same time the same packages (except usplash) would be installed again. I, of course, refused :) Later when I re-tried it, I accidentally shut down the terminal and then run dpkg-reconfigure -a. Anyway, if there is nothing that can be done... I give up on this :(

---

