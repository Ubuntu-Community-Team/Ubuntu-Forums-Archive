---
title: "Kernel modules"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by caravel on 2008-12-14
How do I check if kernel modules are unused and if so how do I remove them?  I have installed a new motherboard and Ubuntu has booted up ok, nut I've noticed at start up that a few drivers are loaded but no hardware is found.  Any ideas?

Thanks in advance.

---

### Post by 67GTA on 2008-12-14
You can check which modules are being loaded by running ```
lsmod
``` in a terminal. I don't know any way of just listing unused modules. Most of the time, modules aren't loaded if dependant hardware isn't found. I would use Google and lsmod to find out what each module controls, and weather you need it. If you aren't careful, you will hose your system. To keep a module from loading at boot, you can add it to /etc/modprobe.d/blacklist. If you wanted to keep the ath_pci module from loading, you would add ```
blacklist ath_pci
``` to the end of the blacklist file. If you want, you can post the output of ```
lsmod
``` and ```
lspci -kvv
``` here, and I might be able to help you narrow it down.

---

### Post by caravel on 2008-12-24
Thanks for the help but I ended up reinstalling - it's a long story.

---

