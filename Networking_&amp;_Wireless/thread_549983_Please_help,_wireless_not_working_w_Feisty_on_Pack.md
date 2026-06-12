---
title: "Please help, wireless not working w/ Feisty on Packard Bell Easy Note"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by cigrainger on 2007-09-13
I installed Feisty on my girlfriend's Packard Bell EasyNote R8. It has the stock internal wireless card and an external BT Voyager 1065 wireless card. Both are acknowledged by Ubuntu, but neither can read any wireless signals. We have a cable router that works for all other computers in the apartment, but sitting right next to the router, Ubuntu will not read any signal.

When I try to enter the name of the network, the password and type of security manually, it still won't connect or even acknowledge that a wireless network exists. There are several wireless networks that leak into our apartment, the cards are picking up none of them. I've tried tips from other threads on how to get the BT Voyager card to work, but nothing helps -- it seems dead in the water.

I should also note that both wireless cards worked with Windows perfectly.

Is there something I'm missing here? Can anyone help? Thanks!

---

### Post by spd106 on 2007-09-13
It would be helpful if you could please post the output of entering these commands in to terminal.
```
lspci
```
```
sudo lshw -class network
```

and maybe describe what you see (if anything) in the Restricted Drivers Manager.

---

### Post by tom1979 on 2007-11-29
Im having the same issue, also on the gf's laptop... 

output of above commands in terminal...

00:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI

 *-network:0 DISABLED    
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wlan0
       version: 00
       serial: 00:10:60:67:32:d4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61 latency=64 module=rt61 multicast=yes wireless=RT61 Wireless

I know it says wifi is disabled, but it says enabled in the network program...

---

