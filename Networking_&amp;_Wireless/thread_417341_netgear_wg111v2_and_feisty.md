---
title: "netgear wg111v2 and feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Skooj on 2007-04-21
I previously had my netgear wg111v2 usb adapter working with ndiswrapper in edgy. After I upgraded to feisty, I was pleased to see that ndiswrapper was no longer required to run this adapter. However, I had some huge issues with it. first of all, the link light will not turn on or blink or whatever. Second of all I couldn't ping my router or any other machines on the subnet (but I could ping my modem). After uninstalling network-manager I could finally ping my router and other machines.

The problem now is that there is ~50% packet loss when I try to ping my ubuntu box from any other machine on the network. I never had this problem with ndiswrapper. I'm just wondering if there is any way to disable whatever driver ubuntu is currently using to control this adapter and revert back to using ndiswrapper instead (Which I currently have uninstalled).

Also, in the network-admin panel thing, it shows wlan0 (the adapter. configured to the current network settings) as well as wmaster0 (which is set in roaming mode. if it's not in roaming it kills all possible network connections). why is this?

Any help fixing the problem and/or explaining the wmaster0 thing is greatly appreciated.

thanks in advance!

---

