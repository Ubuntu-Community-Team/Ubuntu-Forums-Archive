---
title: "having problem with flash plugin-installer, flashplugin-nonfree"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by meteora184 on 2010-05-28
so in a nutshell, i decided to upgrade Ubuntu from 8.04 to 10.04 in order to have it function with my new ipod.  It seems to be having problems that are all tracing to this message:

```
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

what can be done?

on a side note, the computer does not even recognize that my ipod exists.

---

### Post by philinux on 2010-05-28
See the forum sticky in General Help for the flash problem.

---

### Post by marcottebj on 2010-05-28
There are several flash plugin options.  Try removing the one in question completely, and installing a different one.  Just go to the Ubuntu software center and type "Flash".  You'll find a suitable plugin.  
 
If you continue to have issues, I would start to suspect either a corrup install, or bad hardware.  Did you do a fresh install, or simply upgrade from 8.04 to 10.04? 
 
I have to say, I love 10.04, but even upgrading from 9.10, I received some cryptic error messages during the process.  I can imagine you might have issues trying to upgrade.  
 
Perhaps you should consider backing up your files and doing a fresh install, if removing the flash, and reinstalling doesn't work.

---

### Post by philinux on 2010-05-28
> **marcottebj said:**
> There are several flash plugin options.  Try removing the one in question completely, and installing a different one.  Just go to the Ubuntu software center and type "Flash".  You'll find a suitable plugin.  
 
If you continue to have issues, I would start to suspect either a corrup install, or bad hardware.  Did you do a fresh install, or simply upgrade from 8.04 to 10.04? 
 
I have to say, I love 10.04, but even upgrading from 9.10, I received some cryptic error messages during the process.  I can imagine you might have issues trying to upgrade.  
 
Perhaps you should consider backing up your files and doing a fresh install, if removing the flash, and reinstalling doesn't work.

He upgraded as he said in his first post and the answer in in the general help forum sticky. ;)

---

### Post by marcottebj on 2010-05-28
right, but last time I "upgraded" I did a fresh install. "Upgrade" doesn't necessarily mean that you used the update manager.   When I "upgrade" a windows box, I don't install the new version over the old one.  I don't even know if an upgrade from 8.04 to 10.04 is supported. That's quite a jump.

---

### Post by philinux on 2010-05-28
> **marcottebj said:**
> right, but last time I "upgraded" I did a fresh install. "Upgrade" doesn't necessarily mean that you used the update manager.   When I "upgrade" a windows box, I don't install the new version over the old one.  I don't even know if an upgrade from 8.04 to 10.04 is supported. That's quite a jump.

LTS to LTS is a valid upgrade. And the error he's getting matches the bug in the sticky.

Unless he posts back we're stuck.

---

### Post by meteora184 on 2010-05-29
thank you, the post in the sticky worked and I managed to install it using the Ubuntu Software Center so as to my awareness, everything is working.

---

