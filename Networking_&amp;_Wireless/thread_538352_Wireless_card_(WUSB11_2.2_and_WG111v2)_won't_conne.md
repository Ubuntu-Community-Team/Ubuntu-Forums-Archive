---
title: "Wireless card (WUSB11 2.2 and WG111v2) won't connect to network"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by gdudeman on 2007-08-29
A little background: Kubuntu (Ubuntu also installed) Feisty desktop 32 bit, newish machine. Both WUSB11 and WG111v2 usually worked before I moved my computer (they would crash sometimes). Now neither works. I've searched all the threads and I can't find any problems that match mine. I'm sort of a n00b. Here goes:

When WUSB11 is plugged in, it shows networks, but will not connect to the only local network I have access to. My laptop, also running Kubuntu is sitting next to the desktop and is connected and my desktop connects when booted to Vista with WG111v2 (no vista drivers for WUSB11). it shows up with **lsusb as Linksys WUSB11 V2.6 802.11b Adapter**, but in KNetworkManager it shows up as "**Unknown USB Vendor Specific Interface**". When I try to connect via KNetworkManager, it usually hangs at 28% "configuring device" for a while, then just goes to not connected mode. Sometimes it pretends to be connected for 30 seconds to minute before it goes back. An oddity: it has started showing up with the ethernet symbol instead of the wireless one sometimes. I've checked the password 1,000 (plus or minus 800) times forward and backward.

lshw says "...driver=at76_usb driverversion-0.15beta1..."


When the WG111v2 is plugged in, it shows up properly with lsusband even with lshw (as a generic USB device, but product and vendor are correct). Sometimes it will not show any networks at all, but upon restart, it will show the network. KNetworkManager identifies it properly when I click "manual configuration" but it still won't connect to the network! Oftentimes it won't show any networks also.

So I'm at a loss. I hate Vista, but I love the interweb. Any suggestions? I know just enough about linux to screw up my xorg.conf and to sudo my way around.

---

