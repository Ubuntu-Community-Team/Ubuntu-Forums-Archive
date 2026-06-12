---
title: "Feisty Doesn't Recognize Card."
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by kbaum on 2007-05-26
Hi. My HP Pavilion ze5000 laptop has been running Ubuntu for a while, and when it ran Dapper the wireless worked fine. But in both Edgy and Feisty, the wireless card is viewed as another ethernet port, and doesn't work.:(

When I go into the netwrok prefs, it is lised as (wlan0) Ethernet Connection. 

It has a Prism2.5 Wavelan chipset.

Help!

---

### Post by AndyCinDallas on 2007-05-26
My wife has the same laptop, but she has the Broadcom chipset - all I did was download and install the file mentioned [here](http://ubuntuforums.org/showthread.php?t=197102), rebooted and it worked. I don't know about the Prism chipset, I'm afraid.

---

### Post by chili555 on 2007-05-26
This:> all I did was download and install the file mentioned hereis not for you. You need the right action for the right chipset.

Please do:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism2
```If you get a few words of text from every command, then too many modules have been loaded and they are fighting instead  of working. Please *sudo gedit /etc/modprobe.d/blacklist* to add the following on its own line:```
blacklist prism2_<whatever_you_found>
```It may be prism2_cs or prism2_pci or otherwise. You can leave off the .ko extension. Save and close gedit and reboot. You should be good to go. Post back and let other Prism2.5 fans the outcome.

---

