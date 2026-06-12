---
title: "Aircrack-ng"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by ScarF4ce on 2008-01-12
hey all, im new to ubuntu (installed 4 hours ago for the sole purpose of aircrack) and this is my first post indicating i have a problem :(

when following this tutorial: 

[http://www.grape-info.com/doc/linux/config/aircrack-ng-0.6.html](http://www.grape-info.com/doc/linux/config/aircrack-ng-0.6.html)

i scrolled down to how to crack wpa-spk using airodump (near the bottom of page) and it asked me to type in the command: 

**airmon-ng start wifi0** [i only just found out you have to put *sudo* infront (utter n00b here)]

this brought up this:

ath0            Atheros         madwifi-ng VAP (parent: wifi0)
ath1            Atheros         madwifi-ng VAP (parent: wifi0)
ath2            Atheros         madwifi-ng VAP (parent: wifi0)

then the tutorial said to type in this:

**airmon-ng start ath2** which brought this up:


Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
ath0            Atheros         madwifi-ng VAP (parent: wifi0)
ath1            Atheros         madwifi-ng VAP (parent: wifi0)
ath2            Atheros         madwifi-ng VAP (parent: wifi0) (VAP cannot be put in monitor mode)

now if im not mistaken if i cant put the interface into monitor mode i cannot go onto crack WPA-PSK. Here lies my nooby problem :]] thx in advance

---

### Post by kevdog on 2008-01-12
Try deleting all the ath virtual interfaces

For example

sudo wlanconfig ath0 destroy

Then recreate the monitor mode interface.

---

### Post by ThomasNovin on 2008-06-27
For the record, this works.

AFAIK in Hardy this doesn't work any longer because of usage of a new open-source driver. I downloaded & installed the latest gutsy kernel and then you're back to the atheros driver.

---

