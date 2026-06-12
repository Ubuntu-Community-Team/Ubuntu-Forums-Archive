---
title: "virtual box"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by pramodmmuraly on 2009-01-11
i am trying to install solaris 10 on ubuntu 8.04 using virtual box.but on starting following error is showing


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 i dont know which driver to be installed.
plz help me on this

---

### Post by RomeReactor on 2009-01-12
Hi. Which version of VirtualBox do you have installed? If you installed it from the repositories, try installing the **virtualbox-ose-modules** as the error suggests.

Or try uninstalling it, and get the newest version form [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by physeetcosmo on 2009-02-04
> **RomeReactor said:**
> Hi. Which version of VirtualBox do you have installed? If you installed it from the repositories, try installing the **virtualbox-ose-modules** as the error suggests.

Or try uninstalling it, and get the newest version form [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

How can I uninstall virtualbox if i had installed it from a downloaded package? It's version 2.1.2 and (obviously) isn't listed in Synaptic. I tried using:

```
sudo apt-get remove virtualbox
```

To no avail. Any help would be great, thanks!:D

---

### Post by kestrel1 on 2009-02-04
Have you added your username to the virtual box users (vboxusers) group?

---

### Post by physeetcosmo on 2009-02-04
> **kestrel1 said:**
> Have you added your username to the virtual box users (vboxusers) group?

Thanks for the swift response kestrel1. I found the proper command i need to use:

```
sudo dpkg -r virtualbox-2.1
```

Apparently if a package is installed with a .deb, it needs to be removed that way as well. :)

---

### Post by pramodmmuraly on 2009-02-07
thank you dude
 i ve installed virtual box from the link and is working fine thanks for the help

---

