---
title: "Error: No such partition, grub rescue&gt;"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by jbird1 on 2011-07-16
Hi

I recently purchased an EeePC 901 secondhand, from a trusted friend. Not liking the specialised linux already on there, i removed it and replaced it with Windows 7. However, this Netbook could not seem to run 7 very well, so i partitioned it with Xubuntu.

Seemingly due to partition space, i had problems with Xubuntu when it tried to update, leading me to reinstall several times. At one point during trying to reinstall, the installation broke, stating that it could not install the bootloader. 

Now, whenever i boot, even from USB, it does not do anything, it says: "Error: no such partition, Grub Rescue>

---

### Post by coffeecat on 2011-07-16
Hi and welcome to the forum.

If the installation broke when you last tried to install, it may be that only a re-installation is going to fix this, but let's have a look at what's on your system first. Boot up with your live Ubuntu USB and choose "try Ubuntu". That is, boot up to the live desktop, not the installer. Now go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity.

**EDIT**: sorry, forgot to comment on this:

> **jbird1 said:**
> 
Now, whenever i boot, even from USB, it does not do anything, it says: "Error: no such partition, Grub Rescue>

Check you BIOS settings and ensure that it is set to boot from the USB. That error message means it is trying to boot from the internal drive. The EeePC BIOS has a habit of changing the boot order when you're not looking.

---

