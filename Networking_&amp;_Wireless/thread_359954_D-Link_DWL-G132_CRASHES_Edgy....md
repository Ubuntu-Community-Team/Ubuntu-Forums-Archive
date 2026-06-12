---
title: "D-Link DWL-G132 CRASHES Edgy..."
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by koolkid64us on 2007-02-12
Yea, Whenever I try to make that wireless card work in Edgy, the system hangs.  I also have this problem in Linux Mint Bianca and the latest Knoppix.  I think they're all related somehow, because when I hit that "modprobe ndiswrapper", the system will hang.  This happens with the version of Ndiswrapper that comes with the distro.  I've really noticed this in Edgy, Ubuntu Edgy more specifically.  Any Ideas?

FYI, I run a:

P4 1.8 GHz
1.5 GB SDRAM
ATI Radeon 9200 SE Video card with 128 MB Video RAM
D-Link DWL-G132 Wireless USB Dongle (Atheros Chipset)
SB Audigy 2 Sound Card
Currently in Xubuntu 6.06 Dapper (For my Linux Fix).

:confused: :confused:

---

### Post by Metaljaz on 2007-02-13
blacklist the native drivers that were installed with the distro. then reboot

---

### Post by koolkid64us on 2007-02-15
Umm....  How would I go about doing that?:confused:

---

### Post by Metaljaz on 2007-02-15
Run this command and see if the driver you installed is the driver trying to be used
by ndiswrapper:

sudo ndiswrapper -l

If it is the wrong driver it will need to be blacklisted. 
Add the driver to the bottom of:

/etc/hotplug/blacklist

by typing in the terminal window

sudo gedit /etc/hotplug/blacklist

Ubuntu maybe trying to load this driver: orinoco_pci
Not the right one. If that is the case that is what you
will add to the bottom of the file and save it.

---

