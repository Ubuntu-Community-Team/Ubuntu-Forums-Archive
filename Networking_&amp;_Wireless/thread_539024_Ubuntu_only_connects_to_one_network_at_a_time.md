---
title: "Ubuntu only connects to one network at a time"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by ubunteduser on 2007-08-30
I have an Ubuntu Feisty desktop setup with 2 lan and 1 wireless going to different networks and not in roaming and with dhcp.

Only one can be on at a time. I need access to more than one. I think that Ubuntu desktop is configured out of the box to only connect to one network.

What do you do to get around this?

Edward Ing

---

### Post by wirelessmonkey on 2007-08-30
All can be on at a time, but Ubuntu, like most other OSs sets interface priority.  What exactly are you trying to do?  Some applications allow you to specify a network interface to work over.

---

### Post by netztier on 2007-08-31
> **ubunteduser said:**
> I have an Ubuntu Feisty desktop setup with 2 lan and 1 wireless going to different networks and not in roaming and with dhcp.

Only one can be on at a time. I need access to more than one. I think that Ubuntu desktop is configured out of the box to only connect to one network.


Thats a know limitation of network-manager: it allows for only one active interface at a time.

You can exempt NICs from being managed by network-manager by configuring them in /etc/network/interfaces.

Suggestion: leave the WiFi NIC managed by network-manager, because it handles WPA-(2) etc nicely, and configure the wired NICs for DHCP via /etc/network/interfaces, and disable the WiFi NIC via GUI when not needed.

best regards

Marc

---

### Post by reckless2k2 on 2007-08-31
i think you are just looking to use hotplug which is not installed by default i believe. you have to do a quick edit of the interfaces file but it will allow you to jump back and forth between networks such as wireless or hard-wired depending on whether a cat cable is plugged in or not. i think that's what you are looking for.

---

