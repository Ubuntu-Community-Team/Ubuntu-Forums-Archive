---
title: "How to uninstall Clairodock?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by retskrad on 2009-01-01
installed it from this site:

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

> Installation

The project is split in to two parts: the dock itself and the plug-ins. Only the installation of the dock is explained, but installing the plug-ins is the same, just make sure you install the plug-ins after the dock.

The config file will not be overwritten during updates as Cairo-Dock is capable of inserting the missing fields if any without losing your previous settings.

Please note that, although Cairo-Dock is listed in the Universe repository since Ubuntu 8.10 (Intrepid Ibex) and can be installed using Synaptic Package Manager, it is recommended to install Cairo-Dock using one of the methods described below to get the most up-to-date and stable version of Cairo-Dock.

From the Repository (Stable)

This is only for Ubuntu 7.10 (Gutsy Gibbon) 32 bit, Ubuntu 8.04 (Hardy Heron) 32/64bit and Ubuntu 8.10 (Intrepid Ibex) 32/64bit.

To add the Cairo-Dock repository to your sources open the sources.list file:

sudo gedit /etc/apt/sources.list

and add the appropriate repository to the end of the file:

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) gutsy cairo-dock

The signed GPG key for identification of the repository is:

wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

Then, to install Cairo-Dock, issue these two commands in the terminal:

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

There are no repositories available for releases older than Ubuntu 7.10 (Gutsy Gibbon). So, if you want Cairo-Dock for an older release, you must compile it or download the package. 

But now, when I look in Add/remove programs, I can't find clairo, what should I do?

---

### Post by Tim Sharitt on 2009-01-01
In a terminal
```
sudo apt-get remove cairo-dock cairo-dock-plug-ins
```

---

### Post by retskrad on 2009-01-01
Thanks man, appreciate it.

---

