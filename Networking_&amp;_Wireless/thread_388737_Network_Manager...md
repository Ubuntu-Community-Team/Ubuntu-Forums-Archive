---
title: "Network Manager.."
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by steevz on 2007-03-19
Alright, so I am very new to Ubuntu and Linux for that matter so any help at all would be great.

The problem I am having is that I can't install the Network Manager.. and it should be included with Ubuntu I'm pretty sure. I type:

sudo apt-get install network-manager-gnome

And it says that the package cannot be found. I also downloaded the i386 version of it and it came as a .deb file. I tried double clicking this file and it didn't work. Do I need to enter something into the terminal to execute this file?

Help please..

---

### Post by nathanhillinbl on 2007-03-19
I'm new to all this too, but i can tell you that when you click on the .deb package, it should prompt you for an admin password, to run GDebi Package Manager then it will install it by itself, so theres gotta be something wrong there. I just dont know what.

---

### Post by steevz on 2007-03-19
Okay, when I double click on the .deb file the error message I get is:

Error: Dependency is not satisfiable: libdbus-1-3

And I cannot install it.

---

### Post by steevz on 2007-03-20
Alright. I fixed my problem and did so by:

In terminal:
sudo aptitude install network-manager
sudo apt-get install network-manager-gnome;
Reboot.

On reboot I had the Network Manager on the top right of the toolbar. 

Internet now works great.

---

