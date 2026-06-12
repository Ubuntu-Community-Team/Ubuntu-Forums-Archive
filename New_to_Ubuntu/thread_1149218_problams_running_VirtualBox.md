---
title: "problams running VirtualBox"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by funkfresh01 on 2009-05-05
VirtualBox 2.2.2 was running fine until, I got the latest upgrades from Ubuntu and now when I try to run Vista via VirtualBox. VirtualBox refuse to run. VirtualBox told me to execute  the /etc/init.d/vboxdrv setup.  I executed the command, and it failed. I looked inside the VirtualBox log files and found this:

Makefile:140: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

What I understand from the error is that Virtual Box could not find the current Linux kernel. That is what I understand.  How do I fix this problem?

---

### Post by kpkeerthi on 2009-05-05
You should run it with sudo ```
sudo /etc/init.d/vboxdrv setup
```

To install the linux kernel source, look for package **linux-source** in synaptic. For other build and related support tools, look for **build-essential** and **linux-headers** in synaptic.

---

### Post by Cresho on 2009-05-05
#sudo apt-get install dkms

without the # sign plese4


This fixes my linux kernel update and updates virtualbox accordingly and seemlessly.

---

