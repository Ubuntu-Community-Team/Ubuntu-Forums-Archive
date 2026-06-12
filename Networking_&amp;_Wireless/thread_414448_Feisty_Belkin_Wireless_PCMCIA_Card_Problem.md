---
title: "Feisty Belkin Wireless PCMCIA Card Problem"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by dstubb on 2007-04-19
OK...curiosity got the best of me and I updated to Feisty over the weekend....everything went well except that now my Belkin Wireless Card, 802.11b model F5D6020 (which was recognized no problem and worked great in Edgy) no longer shows up in the Network control panel. Wired networking works fine. I also tried a Proxim card this morning that a friend had and it also doesn't show up.

How can I get my Belkin card to work again?

Computer is a Dell C800 laptop.

This is the output of sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth0
       version: 10
       serial: 00:01:03:88:d1:30
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.0.1.10 latency=32 link=yes maxlatency=5 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:f8ffdc00-f8ffdc7f iomemory:f8ffd800-f8ffd87f irq:10
[B]  *-network UNCLAIMED
       description: Ethernet controller
       product: Wireless PCMCIA Card - F5D6020
       vendor: Belkin
       physical id: 1
       bus info: pci@07:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:3c000000-3c0001ff irq:10[/B]

---

### Post by serkanyavash on 2007-05-10
HELP! 

This is the most frustrating thing I have ever experienced! 
My network card (wireless-belkin F5D6020-3000uk) was working untill i did the update on ubuntu 7.04. I did the download then shut my IBM 600E. the next day when i started it it said no network device founf.
yet, under the hardware devices it lists it!
I have looked around and tried to install ndiswrapper (which was supposedly on the disk-but is not) and failed miserably! And now i'm stuck! 
I wouldn't be bothered if it hadnt been working but IT WAS! I can not be going crazy, i'm still young!

P.S. if you hadn't already figured it, I am a NOVICE! 

Please please help! I am desperate!

---

### Post by tutti13 on 2007-05-13
I have the same proble.  Never had any problems with Dapper.  Wireless got even better with Edgy.  Every setup was automatic......till Feisty

---

### Post by serkanyavash on 2007-05-24
ok, i have withered it down to one problem...

My belkin card is disabled! but the $1000 question is how to enable it. I am using a ibm thinkpad 600e. Any suggestions are more than welcome.

---

### Post by tutti13 on 2007-05-26
You aren't kidding.  Tried using ndiswerapper with the original drivers, and it goes like irq11 being shut down.  You know if it had never worked, I would have felt better than the current situation where the card has somehow deactivated.

---

### Post by tutti13 on 2007-05-26
OK, finally got my Belkin F5D6020 v3 wireless card going.  Need to make use of ndiswrapper, probably the most recent version would be the best. 2 files need to be put into /usr/sbin before running ndiswrapper.  They would be Bel6020.inf coming from the cd coming with the card.  The other would be rtl8180.sys coming from [www.realtek.com.tw](www.realtek.com.tw).  Type in 8180 in a search box to get a zip-file with the namendis5x-8180(173).zip.  Extract that zip file to get rtl8180.sys.  Gedit Bel6020.inf so that all references in the file to Bel6020.sys are changed to rtl8180.sys.  Save Bel6020.inf with the changes to reference and then run ndiswrapper as described in ubuntu forums.  Belkin card works well if working.

---

