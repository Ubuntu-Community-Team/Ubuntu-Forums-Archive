---
title: "help - can't see network"
date: 2004-11-06
forum: Networking &amp; Wireless
---

### Post by Tapeworm on 2004-11-06
I have a Shuttle SS50 computer that has a built in Realteck NIC.
According to the spec sheet for my system it is a 8100b

The NIC is detected in Device Manager as RTL -8139/8139C/8139C+

When I go to configure the network connection, the checkmark in the active column will not stay. 

attached is the results of  lsmod


I am a new UNIX user and don't know what to check next.

Any ideas/suggestions?

---

### Post by metron on 2004-11-07
It sounds like your interface is detected, but not configured. Try running dhclient3 in root console. It's also possible you may have to configure your interface manually if your network doesn't support dhcp. What kind of internet connection do you have? Do you have a router? Did you have it working in Windows previously?

---

### Post by Tapeworm on 2004-11-07
[QUOTE=metron]It sounds like your interface is detected, but not configured. Try running dhclient3 in root console. It's also possible you may have to configure your interface manually if your network doesn't support dhcp. What kind of internet connection do you have? Do you have a router? Did you have it working in Windows previously?[/QUOTE]

cable modem using DHCP. no router. haven't tried windows on this hardware but another computer works fine with this connecton using WinXP or the Warty Live CD. 

It would suck if this is a hardware problem...

attached is the results of dhclient3

Thank you for your help.

Tapeworm

---

