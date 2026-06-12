---
title: "Zcomax 325HP+ and Fiesty No IVs or great Tx power"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by Va15a11a on 2007-09-24
Hello,
I have recently purchased a Zcomax XI-325HP PCMCIA card and am having trouble configuring it to work correctly and also am having trouble configuring it to work properly with Kismet etc.

Known Problems:
-in iwconfig the card is labeled under eth2 and shows as "Prism I"
-Works to connect to standard WiFi networks, but less range than my built-in
-Can put into Monitor mode but does not pick any IVs in Kismet
- lsmod | grep orinoco, lsmod | grep hostap produce results but lsmod | prism2 does not
-in /sys/bus/pcmcia/drivers, I have orinoco_cs and hostap_cs

If there is any help that anyone could provide me to get this working properly, I would be very grateful. 

Thank You in Advance

---

