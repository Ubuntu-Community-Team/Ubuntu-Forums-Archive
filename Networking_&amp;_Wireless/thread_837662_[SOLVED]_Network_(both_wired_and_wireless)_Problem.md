---
title: "[SOLVED] Network (both wired and wireless) Problems in 8.04"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Kaneda on 2008-06-22
So, I just updated to Hardy Heron, and I can't connect to the internet anymore.  Things worked fine in 7.10.

Here is my hardware info from lshw -C network:
```

id:		network
description: 	Ethernet controller
product: 	82573L Gigabit Ethernet Controller
vendor: 	Intel Corporation
physical id: 	0
bus info: 	pci@0000:02:00.0
version: 	00
width: 		32 bits
clock: 		33MHz
capabilities: 	pm msi pciexpress cap_list
configuration:	latency	= 0

id:		network
description: 	Network controller
product: 	AR5418 802.11abgn Wireless PCI Express Adapter
vendor: 	Atheros Communications Inc.
physical id: 	0
bus info: 	pci@0000:03:00.0
version: 	01
width: 		64 bits
clock: 		33MHz
capabilities: 	pm msi pciexpress msix bus_master cap_list
configuration:	latency	= 0

```

ifconfig doesn't show anything but the lo local loopback.  (no eth0, wlan0, etc.)

I have madwifi installed.

The physical on/off switch for the wireless on my laptop is turned to ON, but the wireless LED indicator is OFF.

Bluetooth is on and working normally.

I did not have any network problems in Gutsy Gibbon aside from Network Manager being buggy every so often.

iwconfig brings up the following:
```

lo	no wireless extensions

irda0	no wireless extensions

```


I just tried rebooting with my computer plugged into the router through a wired connection and now the wired connection is showing up on ifconfig (although it didn't show up when I plugged it in before rebooting).

Any help would be appreciated.  Thank you!

---

### Post by Kaneda on 2008-06-23
Well, I got things working.  Although I had madwifi installed, I tried reinstalling the newest drivers using the guide at #4 [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi").

I found this answer thanks to Ayuthia in [this post]("http://ubuntuforums.org/showthread.php?t=819373&highlight=AR5418").  Thanks Ayuthia!

---

