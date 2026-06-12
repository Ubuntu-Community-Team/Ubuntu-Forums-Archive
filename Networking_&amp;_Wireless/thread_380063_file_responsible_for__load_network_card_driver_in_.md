---
title: "file responsible for  load network card driver in Xubuntu"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by vozhyk on 2007-03-09
Hey,

does anybody know which file is responsible for loading Network card drivers in Ubuntu/Xubuntu?

/etc/modules.conf -- doesn't exit on my Xubuntu installation.

Should it be like this?

Many thanks,

Ales.

---

### Post by kerry_s on 2007-03-09
Try looking under /etc/network.

---

### Post by vozhyk on 2007-03-09
> **kerry_s said:**
> Try looking under /etc/network.

Tried.

/etc/network/interfaces -- set DHCP or Static IP settings,


But not for specific driver settings

---

### Post by chili555 on 2007-03-09
/etc/modules loads modules at boot time. However, if you are trying to load new_module and the kernel has been using old_module, you will need to sudo rmmod -f old_module and add it to /etc/modprobe.d/blacklist.

You may have better luck if you link the module to the interface you are working with in /etc/modules: ```
alias wlan0 new_module
``` Then run sudo modprobe new_module followed by sudo depmod -a.

I would then sudo /etc/init.d/networking restart and check lsmod to see the presence of new_module and the absence of old_module.

---

