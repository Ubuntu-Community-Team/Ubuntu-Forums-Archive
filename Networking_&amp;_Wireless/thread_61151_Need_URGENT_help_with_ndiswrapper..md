---
title: "Need URGENT help with ndiswrapper."
date: 2005-08-30
forum: Networking &amp; Wireless
---

### Post by bttfpromo on 2005-08-30
Okay, I need to install a wireless adapter and ndiswrapper is listed in the package manager, but needs to be installed. I currently don't have an internet connection set up and need ndiswrapper to set it up.

---

### Post by bionnaki on 2005-08-30
just downloaded them from here from a friends computer or cybercafe or college library:

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

---

### Post by az on 2005-08-30
They already thought of that.

The ndiswrapper module is already on your machine and the ndiswrapper command-line tool is is a package called ndiswrapper-utils which is o your install cd.

Just install ndiswrapper-utils, and you are good to go.

sudo ndiswrapper -i (filename.inf)
sudo modprobe ndiswrapper

---

