---
title: "Kubuntu feisty wireless how-to?"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by twidget on 2007-05-24
hi 
i just upgraded to kubuntu feisty from edgy. In edgy my wireless card worked as long as i logged into wireless assistant and manualy connected each time i wanted to connect to the internet. now that i have feisty installed , i dont have wireless assistant anymore and knetworkmanager was broken from the time of install. I have installed kwifimanager. i can see signal strength but the damned thing wont connect. I have tried going into network settings and configuring the card there. by twiddling with both kwifimanager and the network settings i sometimes manage to get connected to the internet but the connection dies when i reboot and i have to fiddle with things for an hour to get it working again.whenever i try and configure the card through network settings i get an error saying that there is something wrong with my ip address. also the settings disappear on reboot. does anyone know how to correctly set it up so that i can connect properly on startup? I'm using an atheros based pci card if that helps any.

---

### Post by twidget on 2007-07-22
figured out at least part of the problem. if i go into the configuration editor and click activate on config 1 and then go into systems settings > network settings > administrator mode and disable and then re-enable ath0 i can connect to the net. i get a strength reading before i do the disable reenable thing so it is connecting the card so i'm thinking maybe its a dhcp thing? 
Also ive got the "load preset configuration at startup" checkbox checked but i still have  to go in and activate it is there a fix to this?
there is also a place where you can get it to run a script on connection, could anyone tell me which commands to use to disable and then re-enable my wireless card?
i dont think this is a kwifimanager problem because when i used it on my first linux install (slackware 10.2) with an atheros card and madwifi, it worked perfectly. and that was a couple years ago.

---

### Post by twidget on 2007-07-22
other things i should add:
1) when kwifimanager first comes up: it has a stength reading but no local ip address once i do the disable/ re-enable  thing it re-connects to the same essid on its own and this time it has an ip address.
2)running sudo ifconfig wifi0 down and then sudo ifconfig wifi0 up shuts down the interface but it doesnt re-connect on its own like it does if i do the disconnect re-connect thing.

---

