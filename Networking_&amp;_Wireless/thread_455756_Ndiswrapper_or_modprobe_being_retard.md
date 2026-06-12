---
title: "Ndiswrapper or modprobe being retard?"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by firestrife2382 on 2007-05-26
every time i reboot my wifi is not connect and i have to issues this command "sudo modprobe ndiswrapper" then it's up and working and it's so &*(^(*^ annoying, is there's any way to fix this?

---

### Post by RomeReactor on 2007-05-27
Hi. Please open a terminal (Applications-->Accessories-->Terminal) and enter the following:
```
gksudo gedit /etc/modules
```
Is **ndiswrapper** there? If not, add it at the end of the file (to load ndiswrapper automatically at boot time), save the file, close Gedit, and reboot.

---

### Post by firestrife2382 on 2007-05-27
it's not there, I added it as u suggested and it worked, thanks! i thought *ndiswrapper -m* handles this kind of stuff.

---

### Post by RomeReactor on 2007-05-27
Well, according to ndiswrapper's manual (man ndiswrapper-1.9):
> **ndiswrapper -m** writes an alias for wlan0 (default wireless device) into module configuration file so that ndiswrapper kernel module is loaded automatically when this interface is used.
so it would seem that would make ndiswrapper load upon boot, but I think it just loads the module when doing a **sudo ifdown wlan0** and/or **sudo ifup wlan0**. In any case, I just add ndiswrapper to /etc/modules after **sudo modprobe ndiswrapper** and **sudo ndiswrapper -m** and it's been fine from then on.

---

