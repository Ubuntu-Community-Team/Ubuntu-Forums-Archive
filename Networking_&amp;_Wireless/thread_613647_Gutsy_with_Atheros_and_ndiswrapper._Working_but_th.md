---
title: "Gutsy with Atheros and ndiswrapper. Working but the system is slow"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by mikseven on 2007-11-15
Hi Guys, 

I'm running Gutsy on a Thinkpad T60 with Atheros AR512. 
Wireless is working with ndiswrapper but the system si slow. I can see the cpu usage always on 100%.

If I unload the ndiswrapper, system works fine.

Any suggestion?

Thanks in advance

---

### Post by mikesignguy on 2007-11-15
you need to go some more research ...i use a PMCIA card in my laptop .. can't remember the packages to install it , but i think they are supported by the Kernel

If i remember correctly
ndiswrapper was designed to install drivers for devices that where not available in Linux

sorry if this doesn't help,

---

### Post by mikseven on 2007-11-16
Yes.

Gutsy recognizes the device with the embedded HAL Driver, but doesn't work. I can see the network but I've to submit the txpower command every time to increase its value and it works only for few minutes.

The only way to get wireless working is using ndiswrapper but the system is so slow with it.....

---

### Post by mikseven on 2007-11-16
I've tried to use madwifi and madwifi-ng downloaded from madwifi.org.

The first works exactly as the embedded driver (txpower problems).
The second seems to set the correct txpower value but i can't connect to ap and every time I start the pc it cretaes a new interface.

Only ndiswrapper seems to work but it slows down the system,

Anny suggestion.

Thanks
Mik

---

