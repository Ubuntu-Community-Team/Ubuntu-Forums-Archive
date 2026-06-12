---
title: "[SOLVED] How do I disable ndiswrapper in favor of acx module?"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by peterdm on 2008-07-21
When I installed Ubuntu on my system, it used the acx driver for my ACX 111 wireless chipset by default. Because I needed WPA, I started messing around with ndiswrapper and the windows drivers. Now it loads ndiswrapper, but I want to revert to the acx driver without uninstalling the ndiswrapper driver. Basically when I do "sudo rmmod ndiswrapper; sudo modprobe acx" this has the desired effect, but I want to convince the system to start up in this configuration rather than having to type it manually. How does ubuntu decide to load ndiswrapper in the first place? When looking at /etc/modules, it does not contain ndiswrapper... So how does Ubuntu decide which modules to load at startup?

---

### Post by rogier.de.groot on 2008-07-21
My laptop has a file /etc/modprobe.d/ndiswrapper for loading ndiswrapper. Maybe if you moved it to another directory.

---

### Post by peterdm on 2008-07-27
Indeed that works...
This is still a bug in the uninstaller of ndiswrapper: even when I uninstall ndiswrapper with the option "completely uninstall" the config file still stays there.

Peter

---

### Post by WhiteHorse on 2009-05-03
I can confirm this bug in 9.04 as well. For some reason the /etc/modules.d/ndiswrapper file is not removed when one uninstalls ndiswrapper from within Synaptic.

---

