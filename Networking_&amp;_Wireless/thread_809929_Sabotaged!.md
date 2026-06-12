---
title: "Sabotaged!"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by ManBlue on 2008-05-27
HElP please. Yesterday (May 26th) I did the update Ubuntu provides on the tool bar and now I don't have wireless network anymore. What did they do to me?:confused:

---

### Post by dmizer on 2008-05-27
what did you do to get your wireless working in the first place?

please post the output of:
```
lshw -C network
```

---

### Post by ManBlue on 2008-05-28
The way I fixed it the first time was to install Ubuntu 8.04 over 7.10. I installed, rebooted, it worked. I installed the updated and it stoppd working. The wireless network selection is subdued now. won't let me select it. This is what I got when I typed lshw -C network:
```
WARNING: you should run this program as super-user.
*-network description: Ethernet 
interfaceproduct: MCP67 
Ethernetvendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth10
version: a2
serial: 00:1b:24:eb:ce:ff
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bitsclock: 33MHz
capabilities: cap_list
configuration: latency=0
```

---

### Post by sridenour on 2008-05-28
> **ManBlue said:**
> HElP please. Yesterday (May 26th) I did the update Ubuntu provides on the tool bar and now I don't have wireless network anymore. What did they do to me?:confused:

Same thing happened to me on the 27th. I had been using ndiswrapper with out any hitches or problems. Then after update it had switched to the b43(which works at 2400buad speed). Have been trying like crazy to get the system to use the ndiswrapper again but nothing. Also the wireless configuration section in Network Manager is MIA.

---

### Post by dmizer on 2008-05-28
ManBlue,
start here: [http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)

sridenour,
your card is different than ManBlue's.  please post a new thread or look for howto's on broadcomm.

---

### Post by Bartender on 2008-05-28
Do you still have Vista on the laptop?  Apparently Ubuntu isn't necessarily identifying the Atheros card correctly.  I saw an Atheros 5007 identified as an AR242X, just like yours.
If you still have Vista go into Device Manager and find out exactly how Vista identifies your wireless adapter.

After getting the kernel update, these directions
[http://forum.notebookreview.com/showthread.php?t=254244](http://forum.notebookreview.com/showthread.php?t=254244)
worked for me.  This was with an Atheros 5007!  If that's not what you have you'll have to find out the exact directions for yours.

---

### Post by ManBlue on 2008-05-28
That thread did the trick Dmizer,
Thanks

---

