---
title: "ubuntu 16.04 -  wireless - used as hotspot - may get your wifi stuck on hotspot"
date: 2017-11-25
forum: Networking &amp; Wireless
---

### Post by photonxp on 2017-11-25
This just happened to me after I tried to connect to the ubuntu hotspot from an android phone. 

The network would still be shown as in hotspot mode, every time I stopped the hotspot mode in the gnome network settings, closed the setting and then returned to the wireless setting.

I tried to restart the network-manager and reboot ubuntu several times but no effect.

Finally, I got my wifi back by the following steps:
- deleted all my wireless connections
- regenerate wireless connections
- disable the wifi from the upper-right wifi notification list
- opened the gnome network settings
- enable the wifi from the upper-right wifi notification list
- gnome network settings refresh the wifi list
- connect the wifi from the gnome network settings
    
Don't know how exactly this tricky wifi behavior was triggered. And the ubuntu hotspot was always shown as "out of range" on the phone.
Just another treacherous experience with wifi.

---

