---
title: "NIC not found"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Loki*PI on 2008-05-22
Just bought a new box, the MB is ASUS P5GC-MX/1333 has on-board NIC.  Installed from DVD - Feisty 7.04.  
Installed with no problem but OS is not finding the NIC. 

ifconfig shows no eth0 

How do I force a hardware search?  Suggestions?

Thanks

Let table this for now, I'm thinking it is hardware. Back to the dealer tomorrow.

---

### Post by chili555 on 2008-05-22
Usually, when the operating system can't figure out what driver goes with what card, it gives up and doesn't associate a card with a driver with an interface. Let's see if we can help it. In a terminal, please do:```
sudo modprobe atl2
sudo depmod -a
sudo lshw -C network
```Do you see your NIC with a driver=atl2 and logical name=eth0? If so, please see if you can go to System -> Administration -> Network and see if you can enable and configure your interface. If not, please post your *lshw* details. Thanks.

---

