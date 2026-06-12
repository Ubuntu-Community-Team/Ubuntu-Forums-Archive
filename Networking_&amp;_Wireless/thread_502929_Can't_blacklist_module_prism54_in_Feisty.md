---
title: "Can't blacklist module prism54 in Feisty"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by c.dric on 2007-07-17
i'm using ndiswrapper to make my pci card (SMC 2802w) work in linux ... 
in Edgy i had to blacklist prism54 so that it didn't interfere.
in Feisty prism54pci & prism54common are loaded at boot and adding them to the blacklist doesn't help.

i made a startup script to fix this temporarily but i'd like to know how to fix it cleanly ...
any thoughts ?

---

### Post by c.dric on 2007-07-20
bump :redface:

---

### Post by kevdog on 2007-07-20
First make sure the module names are correct.  If the blacklist doesnt work you can physically remove the modules with:

sudo modprode -r *module_name*

---

### Post by c.dric on 2007-08-08
well it looks like the prism54 modules that come with feisty work with my card now (SMC 2802w v2) ... no more ndiswrapper for me :)

i'm still curious about that blacklisting problem tho ...

---

