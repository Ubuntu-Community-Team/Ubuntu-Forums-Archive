---
title: "Remove GUI from server edition"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by rgotten on 2009-05-12
In learning how to use the server edition 8.04 i install on top of it the dektop edition so i have a GUI interface. How do i remove that desktop edition withouth afecting the server edition

DRG

---

### Post by Dynaflow on 2009-05-12
```
sudo apt-get remove ubuntu-desktop
``` (or "xubuntu-desktop," or "gnome-core," or whatever you installed as the desktop)

---

### Post by bodhi.zazen on 2009-05-12
Install the server kernel

Remove gnome .

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Of course you may be best either leaving gnome or re-installing the server edition.

---

### Post by rgotten on 2009-05-12
Well since i am in testing face i would like to unistall dekstop and keep trying to use server, if i am able to survive with command, then i will reformat hard drive and install fresh and clean version to use fully

---

### Post by bodhi.zazen on 2009-05-12
> **rgotten said:**
> Well since i am in testing face i would like to unistall dekstop and keep trying to use server, if i am able to survive with command, then i will reformat hard drive and install fresh and clean version to use fully

I advise you keep the desktop and manage your server applications from the command line in a terminal. When you are comfortable, re-install is likely much easier.

If you have the RAM you could always try the server edition in KVM / VirtualBox / VMWare ;)

---

### Post by bodhi.zazen on 2009-05-12
> **Dynaflow said:**
> ```
sudo apt-get remove ubuntu-desktop
``` (or "xubuntu-desktop," or "gnome-core," or whatever you installed as the desktop)

You can not simply remove the "desktop (ubuntu-desktop) as it is a meta package. You need to manually (see the link I gave).

```
[COLOR=darkred]**sudo apt-get remove ubuntu-desktop**[/COLOR]

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mdetect libindicate0 libsmbios-bin
Use 'apt-get autoremove' to remove them.
[COLOR=green]The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 65 not upgraded.[/COLOR]
After this operation, 57.3kB disk space will be freed.
Do you want to continue [Y/n]?
```See how that does not really remove gnome ?

---

