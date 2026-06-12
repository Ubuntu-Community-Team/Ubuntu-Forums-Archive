---
title: "software download and installation issues"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by bripa on 2010-08-19
hi all,

When installing new software or running update manager, at the end of the installation process I get the following error message: 



E: linux-image-2.6.32-23-generic: subprocess installed post-installation script returned error exit status 1
E: linux-image-2.6.32-24-generic: subprocess installed post-installation script returned error exit status 1
E: grub-pc: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

Then, a new window appear saying "Changes applied" - update is complete - not all changes succeeded. in the detail there are more text but I can't copy it and paste here. I can just add a screen 

thanks in advance for your help.
Paolo

---

### Post by zvacet on 2010-08-19
In terminal

```
sudo dpkg --configure -a
```

---

### Post by bripa on 2010-08-19
thanks ZVACET for your suggestion.

When running dpkg I get:

bripa@bripa-netbook:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.32-24-generic (2.6.32-24.39) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu7) ...
/etc/default/grub: 11: GRUB_CMDLINE_LINUX: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.24.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-2.6.32-23-generic
 linux-image-generic
 grub-pc
 linux-generic

but still errors persists
Can you please give me some suggestions more?

Regards,
Paolo

---

### Post by nstorrs on 2010-08-24
I get the same (both the initial complaint and the attempted fix). Any other ideas would be really appreciated. 

--
Ubuntu Lucid

---

### Post by forteller on 2010-11-07
I get this too! Ubuntu 10.10 64bit.

E: linux-image-2.6.35-23-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured

Please help! I can't uninstall it or update to the latest version.

---

### Post by ark1-87 on 2010-12-08
I have the same problem everytime i install a update or software it errors at the end, Seems to be a error with the kernel, How to fix do I need to recompile the kernel?

---

