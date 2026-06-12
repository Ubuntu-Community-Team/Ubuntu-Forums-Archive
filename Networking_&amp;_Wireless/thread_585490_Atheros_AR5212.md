---
title: "Atheros AR5212"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Dualboy on 2007-10-21
I am a noob, so bear with me. I have done a fresh install of 7.10. My wireless card is a Dlink DWL-G520. Iwconfig id's it as an atheros ar5212/ar5213. I am using the restricted driver that came with gutsy. I can connect to unencrypted ap's. I cannot connect to my ap running wpa. I am hesitant to just start installing drivers and such, as I really don't know what I am doing. The card is a pci card in a desktop system. 

Anyone else have this problem?

---

### Post by Mundu on 2007-10-25
I am experiencing the same problem with a fresh install of Ubuntu 7.10 too. 
Also a PCI Airlink card detected as AR5212/AR5213.

I there a problem with the driver?

---

### Post by Mundu on 2007-10-25
Editing /etc/rc.local with the workaround below seems to have solved my problem:

[http://ubuntuforums.org/showthread.php?t=540101&highlight=ar5212]("http://ubuntuforums.org/showthread.php?t=540101&highlight=ar5212")

I also switched to a static ip address (manual wireless configuration). Click on the wireless icon top right of desktop. That seems to have improved things
drastically.

---

