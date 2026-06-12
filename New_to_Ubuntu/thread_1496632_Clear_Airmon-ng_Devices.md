---
title: "Clear Airmon-ng Devices"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-05-29
I have been trying to use airodump-ng to scan the network, but you need to first configure airmon-ng to set the device into monitor mode. It says I have multiple devices enabled, so I was wondering what command I should use to clear all devices. Or is this something I'm going to have to do for each device. Basically I was wondering how to clear it so it would be like new every time I rerun it? 

I know how to stop individual devices but I don't know if I have gotten them all.
airmon-ng stop wlan0; airmon-ng stop mon0; airmon-ng 

Interface       Chipset         Driver

wlan0           Intel 3945ABG   iwl3945 - [phy0]

---

### Post by daimaru on 2010-05-29
I think you will be better off on the backtrack forums (maybe even with a backtrack install) check the linke here [http://www.backtrack-linux.org/forums/](http://www.backtrack-linux.org/forums/) i have no problem with airmon but it all depends on your hardware. I am using an atheros card wich works very well. Just check the forums for more info on your card.

---

