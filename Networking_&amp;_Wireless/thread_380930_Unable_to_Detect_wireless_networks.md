---
title: "Unable to Detect wireless networks"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by nastavirss on 2007-03-10
I recently installed Edgy Eft on my system.
I have an Intel wireless card. 

The wireless card is not able to detect wireless networks automatically, it is not listing the available wireless networks.

I hope someone can give me a solution to this problem.

---

### Post by nastavirss on 2007-03-10
And i am able to connect to the network by typing in the "SSID" in the networking properties.

---

### Post by mikewhatever on 2007-03-10
You need a network manager to detect different networks. If you type SSID in the properties, that is only good for one default network. To get the gnome NM, type in the terminal: > sudo apt-get install network-manager-gnome
The same can be done from Synaptic.
Once that installs, type > gksudo gedit /etc/network/interfaces and comment out the lines for the default network(put # in the beginning of the line).
Lastly, reboot, and you should have the NM icon in the panel next to the clock.

---

