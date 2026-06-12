---
title: "Enabling Wireless Networking"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Paco009 on 2008-08-03
Hi,

I just downloaded Ubuntu for the first time today, and everything worked great on startup except for my wireless connection. I read the sticky thread and used a terminal to determine that my wireless hardware is detected, it is simply disabled right now. I just need to know the proper commands needed in the terminal in order to enable my wireless networking. Any help would be really appreciated.

---

### Post by superprash2003 on 2008-08-04
please post your lshw -C network output and your iwconfig output

---

### Post by Paco009 on 2008-08-04
Ok, Here goes.

my lshw -c network output looks like this:

*-network
[INDENT]description: Network Controller[/INDENT]
[INDENT]product: BCM94311MCG wlan mini-PCI[/INDENT]
[INDENT]vendor: Broadcom Corporation[/INDENT]
[INDENT]physical id: 0[/INDENT]
[INDENT]bus info: pc:@0000:03:00.0[/INDENT]
[INDENT]version: 01[/INDENT]
[INDENT]width: 32 bits[/INDENT]
[INDENT]clock: 33MHz[/INDENT]
[INDENT]capabilities: bus_master cap_list[/INDENT]
[INDENT]configuration: driver=b43-pci-bridge latency=0 module=ssb[/INDENT]
*-network DISABLED
[INDENT]description: Wireless interface[/INDENT]
[INDENT]physical id: 1[/INDENT]
[INDENT]logical name: wlan0[/INDENT]
[INDENT]serial: 00:1a:73:15:3c:bf[/INDENT]
[INDENT]capabilities: ethernet physical wireless[/INDENT]
[INDENT]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g[/INDENT]

And, my iwconfig output is as follows:

lo[INDENT]no wireless extensions.[/INDENT]
eth5[INDENT]no wireless extensions.[/INDENT]
wmaster0[INDENT]no wireless extensions.[/INDENT]
wlan0[INDENT]IEEE 802.11g ESSID:""[/INDENT]
[INDENT]Mode:Managed Channel:0 Access Point:Not-Associated[/INDENT]
[INDENT]Tx-Power=0 dBm[/INDENT]
[INDENT]Retry min limit:7 RTS thr: off Fragment thr=2346 B[/INDENT]
[INDENT]Link Quality:0 Signal Level:0 Noise Level:0[/INDENT]
[INDENT]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/INDENT]
[INDENT]Tx excessive retries:0 Invalid Misc:0 Missed beacon:0[/INDENT]


There it is. Hope that's all you need to know to help me out. Please keep in mind that I'm a total beginner with Linux, so any detailed instructions would be awesome. Thanks again so much.

---

### Post by superprash2003 on 2008-08-05
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

