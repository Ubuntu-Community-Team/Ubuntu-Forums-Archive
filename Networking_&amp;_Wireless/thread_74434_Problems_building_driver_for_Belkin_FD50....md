---
title: "Problems building driver for Belkin FD50..."
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by r0aming on 2005-10-11
Hi all,

I am new in Ubuntu world and just a days ago I installed the Ubuntu 5.04
distribution. I have a wireless network card with RTL8180 chipset is a
Belkin card. I made this card work with Fedora 3 with driver from
[http://sourceforge.net/projects/rtl8180-sa2400](http://sourceforge.net/projects/rtl8180-sa2400), so I tried to build this
driver in Ubuntu but I am getting complaints about Makefiles that are
not existing in /lib/modules/...../build directory, then I checked that this
directory does not exist in Ubuntu, how could I get this directory tree
in Ubuntu? Or is there anybody there with this same driver built problem?

Best regards and thanx in advance

---

### Post by spd106 on 2005-10-12
To compile anything from source you will need to download/install the build-essentials package. Best to do this through synaptic.
Also have a look around the wiki and search through the forums for the rtl 8180 chipset as it is used on many different cards. eg [http://ubuntuforums.org/showthread.php?t=2681](http://ubuntuforums.org/showthread.php?t=2681)
If you get it working please don't forget to update the [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")

Good luck

---

