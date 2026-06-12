---
title: "Can't enable laptop wifi adapter on new Ubuntu14.04LTS install"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by Stephen_Miles on 2015-06-08
Hi, so I just installed Ubuntu on a Dell Latitude E6400 which was previously running Windows XP, but I can't seem to enable the wifi adapter. There is a switch on the side of the laptop for enabling/disabling wifi, as well as a wifi status indicator on the chassis which lights up when the wifi adapter is turned on. In Ubuntu, however, flipping this switch doesn't appear to do anything.

I've tried a few things to try and figure out what's going on:

Running *ifconfig* only shows eth0 and LO devices, but no wlan0 device.

Running *lshw* shows the following for the wireless adapter:

```
*-network[INDENT=2]description: Network controller
product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f1ffc000-f1ffffff
[/INDENT]

```

I have tried the solution listed here:[http://itsfoss.com/fix-no-wireless-network-ubuntu/](http://itsfoss.com/fix-no-wireless-network-ubuntu/), since it describes my exact situation, however once I get to this step: [IMG]http://itsfoss.itsfoss.netdna-cdn.com/wp-content/uploads/2014/12/No_wireless_Network_Ubuntu_4.jpeg[/IMG]
clicking "apply changes" creates a progress bar in the place of the "revert" and "apply changes" buttons, which seems to get stuck at about 10% and makes no more progress.

Does anyone have some idea what the issue could be? I just installed Ubuntu on a Latitude E6440 last week with none of these problems

---

### Post by wildmanne39 on 2015-06-08
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

