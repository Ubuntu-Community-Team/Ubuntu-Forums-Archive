---
title: "Can't scan for wireless networks in edgy"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by ravalox on 2007-02-05
Hey, I have several Dapper Drake installations and they treat wireless networking with ease, but I have a new edgy eft installation that allows me to wirelessly connect if I manually type in the ESSID of the wireless network.  The network tool won't present me a list of ESSID's and let me select a network to connect to.

---

### Post by spd106 on 2007-02-05
Yeah, this was broken just before Edgy was released, sadly it has not been deemed worthy for fixing yet. Since the path to feisty will it replaced by Network Manager, you might want to try it out now. Just install the network-manager-gnome package. Be advised that static addresses are not supported yet, so you have to use DHCP, but you get WPA support as a bonus.

---

### Post by ravalox on 2007-02-06
Okay, I have the network manager installed; the nm-applet doesn't present anything except the wired connection; I need the wireless information.  It doesn't seem to present it, and I can't seem to figure out how to tell it to present it.

---

### Post by gradedcheese on 2007-02-06
network manager ignores any interface that is found in /etc/network/interfaces.  So you need to edit that file and comment out (ie: put a # in front of) every line that has to do with your wireless interface.  Then run nm-applet and the wireless should show up.

---

