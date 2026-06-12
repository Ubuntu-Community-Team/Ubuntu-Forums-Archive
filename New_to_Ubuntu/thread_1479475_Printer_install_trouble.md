---
title: "Printer install trouble"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by jfls45 on 2010-05-10
I'm trying to install a Canon MP190 printer on Ubuntu 10.04 server edition with installed Ubuntu gnome gui. I found linux drivers on the web but when I go to install them I get this message:

Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cnijfilter-common
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 156kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 171419 files and directories currently installed.)
Removing cnijfilter-common ...
jte@LINUX:~$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cnijfilter-common: Depends: libcupsys2 (>= 1.2.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


So I run apt-get -f install    and I get this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cnijfilter-common
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 156kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


Ok, so what gives. Someone point me in the right direction,

Thanks

Jeff

---

### Post by jfls45 on 2010-05-10
When I try to install the CNIJFILTER_COMMON Package, I get this error:

STATUS: Error: Failed to satisfy all dependencies (broken cache)

Then another window pops up saying to do this... apt-get -f install     which I did once and all it does is remove the broken cnijfilter-common

need some help

---

