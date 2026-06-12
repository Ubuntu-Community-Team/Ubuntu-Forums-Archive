---
title: "Wireless wlan0"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by ajmorris on 2007-04-08
Ok, when i boot up with my wireless card in it takes a while on the "configuring network devices" process. Can i fix this?

also i used my wireless card once. Then the network disconnected and when i tried to reconnect it kept asking for the WEP key, and everytime i put it in it said it was incorrect even though i saved it. Anyway, when that happened i rebooted to see if that would help, now it does not pick up wlan0 at all. I can't dhclient to start it and don't know how else to 'force' my Feisty to start wlan0. also i installed the pcmcia-cs source that the WPC11 linksys card (my wireless card) drivers from their site needed (linux drivers) but still could not install the drivers. Any ideas on how to get the linksys WPC11 drivers to work? or how to get wlan0 working again?

---

### Post by bnuytten on 2007-04-21
One question at a time...
> **ajmorris said:**
> Ok, when i boot up with my wireless card in it takes a while on the "configuring network devices" process. Can i fix this?
This is probably caused by 1) setting up the wifi connection and 2) getting an IP address from a DHCP server. You can speed up the latter by manually configuring your network card. If that is an option - depends on your network setup.

> **ajmorris said:**
> 
also i used my wireless card once. Then the network disconnected and when i tried to reconnect it kept asking for the WEP key, and everytime i put it in it said it was incorrect even though i saved it. Anyway, when that happened i rebooted to see if that would help, now it does not pick up wlan0 at all. I can't dhclient to start it and don't know how else to 'force' my Feisty to start wlan0.
ifdown wlan0; ifup wlan0

> **ajmorris said:**
> also i installed the pcmcia-cs source that the WPC11 linksys card (my wireless card) drivers from their site needed (linux drivers) but still could not install the drivers. Any ideas on how to get the linksys WPC11 drivers to work? or how to get wlan0 working again?
Euhhh... You installed the source but did not install the drivers. With which driver is your network card working than? I guess the driver that came with the distro :-) So no need to compile your own drivers unless you discovered a bug or want to upgrade anyway... Or maybe you have the luxury to have multiple wireless cards 8)

---

### Post by ajmorris on 2007-04-21
i did install the drivers....
the wireless card was screwed up by vista anyway, that is my problem. THe card is dead all thanks to vista.

---

### Post by bnuytten on 2007-04-22
> **ajmorris said:**
> i did install the drivers....
the wireless card was screwed up by vista anyway, that is my problem. THe card is dead all thanks to vista.

Time to fix it with Ubuntu than :) Can you post the output of: ```
 iwconfig wlan0
```

---

### Post by ajmorris on 2007-04-22
> **bnuytten said:**
> Time to fix it with Ubuntu than :) Can you post the output of: ```
 iwconfig wlan0
```

it is beyond fixing i believe. When i put it in a windows box, the add hardware wizard appears, however it is after i have removed the card. In linux, the power and link lights flash on for 1 second then turn off.

iwconfig wlan0 is ```
wlan0     No such device
```

---

### Post by bnuytten on 2007-04-22
> **ajmorris said:**
> it is beyond fixing i believe. When i put it in a windows box, the add hardware wizard appears, however it is after i have removed the card. In linux, the power and link lights flash on for 1 second then turn off.

iwconfig wlan0 is ```
wlan0     No such device
```

This typically the kind of output when the module for your card is not loaded. The name of the module depends on which hardware you have.

---

