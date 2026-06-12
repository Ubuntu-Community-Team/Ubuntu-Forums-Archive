---
title: "Built in wifi not being recognized"
date: 2014-02-25
forum: Networking &amp; Wireless
---

### Post by ihelpyou59 on 2014-02-25
Hello All

I'm running Xubuntu 12.04 on a Dell Latitude D630 laptop, Xubuntu 12.04 was preloaded on it and after about a week and a half, the built in wifi stopped being recognized as an option under the Network Manager. Someone at the Xubuntu IRC pointed me to directions on rebuilding the broadcom drivers needed.

My issue is this, after running the build process via Termianl, it will say that it's done and just seem to hang there. Is this normal? I've tried quittiing out and restarting the machine, but get prompted to start it over again only to get stuck back at the same point.  Please, could use some help here.

Posting what it says when i rerun the process in terminal

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
taicho@taicho-Latitude:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-59-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-59-generic
Building for architecture x86_64
Building initial module for 3.2.0-59-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-59-generic/updates/dkms/

depmod....

DKMS: install completed.
^Cdpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 bcmwl-kernel-source

---

### Post by Bucky Ball on 2014-02-25
Please post the output of:

```
sudo lshw -C network
```

... between [code ] tags [ /code].

---

### Post by ihelpyou59 on 2014-03-02
Sorry to take so long to post reply. I managed to solve the issue I was having. The problem laid not so much with the hardware as i was thinking, but with the broadcom drivers i was trying to install/complie into Xubuntu 12.04. I was able to get in touch with someone that was able to help me install the proper drivers needed.

---

### Post by Bucky Ball on 2014-03-02
Please share the fix if it is not much trouble. It will help others. Thanks.

---

