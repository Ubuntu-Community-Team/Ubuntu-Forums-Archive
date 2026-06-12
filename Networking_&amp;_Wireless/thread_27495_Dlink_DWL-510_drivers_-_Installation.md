---
title: "Dlink DWL-510 drivers - Installation?"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by Next_Gate on 2005-04-16
I have installed ubuntu 5.0.4 on my PC, i have a DWL-510 Wireless card but i can´t browse the internet or my network, My router is a Dlink 624 configured for DHCP so i was wondering what can be happening here.. im a newbie in ubuntu and linux, also im trying to open the System->NEtworking window and it wont open.

I have to install a set of drivers for the network card?... i searched in this link for it and didnt find information:
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

Hope you can help me .. thanks

---

### Post by az on 2005-04-16
[http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)

You will have to use ndiswrapper.

sudo ndiswrapper -i <windowsdriver.inf>
sudo ndiswrapper -l
this will list the cards that it is aware of
sudo modprobe ndiswrapper

Then configure your connection in the networking thingy.

If this works, you will need to add the word
ndiswrapper
to the /etc/modules
file so that the module gets loaded on boot....

---

### Post by jasmuz on 2005-10-04
Azz, i have the same issue, but when i get to the modprobe ndiswrapper, it fails to load,...says i have no such module.

What can i do about it, please message me...i need to solve this for a project.

---

