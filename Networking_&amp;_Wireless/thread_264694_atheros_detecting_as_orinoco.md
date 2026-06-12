---
title: "atheros detecting as orinoco"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by livestockPimp on 2006-09-25
howdy,
i have a box set up and i put a fully working wifi card in it.
it is currently running breezy badger and a 3com network card with an atheros chipset.
the hotplug loads it up on boot as a orinoco which i was told orinocos do from time to time... i then proceded to
rmmod orinoco_pci
rmmod orinoco
modprobe ath_pci
and then it wont come up as an interface... when i list iwconfig nothing is there...
i even tried to rmmod the hotplug and everything else that concerns pci that might affect it that i could seen...
i am new to linux so sorry to waste peoples time if i am fundamentally doing somthing wrong...
thanks in advance for any replies.

---

