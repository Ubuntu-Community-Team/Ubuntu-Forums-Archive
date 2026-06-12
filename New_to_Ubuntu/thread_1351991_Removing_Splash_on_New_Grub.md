---
title: "Removing Splash on New Grub"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by spikoley on 2009-12-11
How do I remove the start up splash screen in the new Grub?  I use to remove quiet no splash and run update-grub in menu.lst.

---

### Post by 73ckn797 on 2009-12-11
Install "startupmanager" from Synaptic. There is a switch to turn off the splash.

---

### Post by spikoley on 2009-12-11
> **73ckn797 said:**
> Install "startupmanager" from Synaptic. There is a switch to turn off the splash.

I installed startupmanager and it did not work.  I think it was because grub.cfg did not have write permissions.

I ended up giving grub.cfg write permissions and removing "splash  quiet splash" from the first entry.  That worked for me.

---

