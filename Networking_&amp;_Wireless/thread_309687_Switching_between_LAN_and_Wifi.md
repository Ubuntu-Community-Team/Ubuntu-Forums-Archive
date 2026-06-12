---
title: "Switching between LAN and Wifi"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by ninjaPants on 2006-11-30
I'm trying to figure out how to switch between my wireless card and my wired ethernet card and coming up empty handed... 

I'm on Edgy, my wireless card is a NovaTech 922W (Ra 2500 chipset). The wired card is a DP83815 (MacPhyter) Ethernet Controller by National Semiconductor Corporation (according to lshw).

I tried network-manager, wifi-radar and connection-manager (none of them worked) with this card before stumbling across rutilt and finally getting the interface to work. I can't seem to be able to stop using the wireless card now. Closing the rutilt application doesn't work, nor does running ifdown ra0. 

With network-monitor in the panel, the ethernet card connects, but the wireless card will take over even after I close rutilt. I could only tell this because I tried to access my router's configuration after closing rutilt and got a prompt for another wireless router's configuration page at the same address. I'm guessing I'll only connect to unsecured networks like this, but I'd like to use the wired card as default and only go wireless if there's no wired connection.

Looking back at that I'm not sure how much sense it'll make to anyone else, so I'll stop here for people to ask questions that might make sense of this junk.

Thanks,
Andrew

---

### Post by pessi on 2006-11-30
It looks like the network-manager is not installed. When the network-manager is not installed Edgy tries to activate all the interfaces even if the interfaces are disabled from the network setup tool.

---

### Post by ninjaPants on 2006-11-30
I thought that might fix it and it did. Thanks a lot!

---

