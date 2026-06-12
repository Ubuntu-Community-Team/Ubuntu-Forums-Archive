---
title: "ndiswrapper problems ind edgy"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by glaeven on 2006-11-05
i have a belkin f5d7050. i had to re-install edgy due to partition issues.

on my other install of edgy, i had ndiswrapper for my adapter and it worked fine. in dapper, it dropped, but it was solid in edgy. i downloaded ndiswrapper-utils, and other dependencies from packages.ubuntu.com, and installed them. i used the community docs to install my router.

when i got to:

> #sudo depmod -a

it worked. then i used:

> #sudo modprobe ndiswrapper

and this came:

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by asedas on 2006-11-10
i had the same problem. the solution i did is:
1. uninstall all ndiswrapper
[via synaptic:
sudo synaptic
Ctrl+F and insert ndiswrapper
uncheck all & apply]
2. download the newest version from:
[http://mesh.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz](http://mesh.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz)
and extract it
3. go to the directory with extracted ndiswrapper and put:
make
sudo make install
4. go to the driver directory with .inf file and put:
ndiswrapper -i driver.inf
[driver.inf is the name of .inf file with the driver]
5. check if it's installed:
ndiswrapper -l
[should be driver installed, hardware present]
6. insert:
sudo modprobe ndiswrapper
7. configure wlan0 interface & enjoy!!

it worked for me with my pentagram hornet and the sis163u driver. hope it'll help...

---

### Post by gmleuty on 2006-11-13
Many thanks asedas, this was just the information I was looking for.
Mike

---

