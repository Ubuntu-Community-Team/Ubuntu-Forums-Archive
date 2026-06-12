---
title: "Router not recognized by rt2500pci"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by torque360 on 2008-07-19
I have a rt2500pci wireless card. The problem I am having is it recognizing my router. I can select roaming and it recognizes other routers. When ever I try my router manually it doesn't show any signal. I do have a shared wpa key but I have made sure over and over that it was correct. How can I get my card to recognize my router? I have followed the documentation, but I already have the wpa supplicant. The only problem I can for see is I can't find the config file for the wpa supplicant. I am thankful for any help you can give me.

---

### Post by torque360 on 2008-07-19
Here is something that might help. When I enter lshw -C network I get:
 *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:0e:3b:08:39:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
It recognizes my card but I can't get on my router. It is a Dynex router and I do have a wpa key.

---

