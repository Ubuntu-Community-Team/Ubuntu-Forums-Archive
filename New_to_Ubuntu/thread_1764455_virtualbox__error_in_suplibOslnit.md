---
title: "virtualbox  error in suplibOslnit"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by trewal5839 on 2011-05-21
when starting a new vm with virtualbox on ubuntu 11.04,


Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

error message comes up, all drivers are installed, how do i get around this problem?

---

### Post by ajgreeny on 2011-05-21
> **trewal5839 said:**
> when starting a new vm with virtualbox on ubuntu 11.04,


Kernel driver not installed (rc=-1908)

[COLOR=Red]Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.[/COLOR]

error message comes up, all drivers are installed, how do i get around this problem?
The bit in red is the information you need to follow, so ```
sudo apt-get install virtualbox-ose-dkms
```followed by ```
sudo modprobe vboxdrv
```should do the trick.  Is that what you have already done and what you mean by "all drivers are installed"?

---

### Post by wildmanne39 on 2011-05-21
> **trewal5839 said:**
> when starting a new vm with virtualbox on ubuntu 11.04,


Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

error message comes up, all drivers are installed, how do i get around this problem?Hi, also a great resource is virtualbox.org it has the manual that tells you all the things that you need for each operating system before you set it up and how to set it up and configuration, and that is one of them.

---

