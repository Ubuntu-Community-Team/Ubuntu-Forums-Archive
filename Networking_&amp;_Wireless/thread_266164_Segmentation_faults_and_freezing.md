---
title: "Segmentation faults and freezing"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by Furious_joe on 2006-09-26
I have a minitar PCI wireless card, using a ralink chipset, with Kubuntu linux. iwconfig detects the card, and it appears as ra0, but whenever I try to interact with it, using iwlist or iwconfig, first the programs return segmentation faults, and if i do it the second time, the program doesn't respond and i have to C^c out of it.

---

### Post by Mr Frosti on 2006-09-26
Try reinstalling these packages. Segmentation faults usually occur after upgrading the kernel, or from other major changes.

You can reinstall the package "iwconfig" by running "sudo apt-get install wireless-tools --reinstall" from a terminal.

---

### Post by unco on 2006-09-29
this might help

[http://www.ubuntuforums.org/showthread.php?t=259355]("http://www.ubuntuforums.org/showthread.php?t=259355")

---

### Post by mysmallsecret on 2006-09-29
i had this same problem with 
iwlist ath0 scan
segmentation fault and then freeze
also dhclient didn't work

i fixed it eventually and reinstalling everything didn't work

i think that the way i did it is disabling all network devices
sudo ifconfig <device> down

then make sure that the line
auto <wireless device>
i.e. "auto ath0"
appears in the /etc/network/interfaces

and then reboot

i hope this works
avery.

---

