---
title: "Unbuntu Server Wireless issues (Fiesy)"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by bbejeck on 2007-05-01
Hi All-
After an exhaustive search of this forum and other sources, I am posting my wireless issues with Ubuntu **Server **, Fiesty Fawn edition.  I am running Fiesty Destop on my Toshiba satellite A100/A105 with no issues so this is extra puzzling to me. 

I have installed Ubuntu server edition on one of my desktops that has a DLink WDA 1320  wireless card.  Prior to installing Ubuntu server, the card worked fine with XP sp2. I am also using a DLink router that is actiing as my DHCP server.  I have a another desktop (XP sp2) and my toshiba laptop (Fiesty Desktop) on this network with no issues.

When I got to the network configuration part of the install, it recognized two interfaces: wifi0 and ath0.  I have reinstalled a couple of times configuriing with both interfaces with no luck.  I get errors saying my network is not using DHCP or no wireless access points can be found.  After install I ran lspci,iwconfig, and ifconfig with the following results:

lspci

Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC 

iwconfig

lo no wireless extensions

ifconfig

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1202 errors:0 dropped:0 overruns:0 frame:0
TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:115302 (112.5 KiB) TX bytes:115302 (112.5 KiB)

Any suggestions? 
Do I need to install wine/madwifi? I can't connect to the internet from this box, so anything I install would have to be manual. 

I also tried the suggestions modifyin various grub boot parameters found here   [http://ubuntuforums.org/showthread.php?t=414550&page=3&highlight=wireless+with+ubuntu+server](http://ubuntuforums.org/showthread.php?t=414550&page=3&highlight=wireless+with+ubuntu+server) with no luck.

-Thanks

---

### Post by bbejeck on 2007-05-02
My problem is solved.  All I had to do was intall madwifi and now my server is on my network.

---

