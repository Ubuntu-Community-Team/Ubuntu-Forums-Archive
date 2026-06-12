---
title: "Edgy Wireless and Linksys Card"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by obrient on 2006-10-29
Okay so I upgraded to Edgy thinking that things would just work. Any ways I found that my wireless once again is broken. I reread all the threads that I could but haven't seen anything that looks like it will work. 

The first problem is I don't see a wlan interface at all and don't know how to make it become an added piece to my networking area. All I see is the modem and eth0. So I guess the first question is what happened to my wlan?

I have a linksys pcmcia card Model #: WPC54G v4

Here is what I have from the following:

lspci -v
```
07:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter
(rev 01)
       Subsystem: Linksys Unknown device 0029
       Flags: medium devsel, IRQ 11
       I/O ports at e800 [disabled] [size=32]
       Memory at f6000800 (32-bit, non-prefetchable) [disabled] [size=32]
       Memory at f6000000 (32-bit, non-prefetchable) [disabled] [size=2K]
       Capabilities: <access denied>
```

iwconfig
```
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.
```

 /ect/network/interfaces
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

lshw
```
*-network UNCLAIMED
         description: Ethernet controller
         product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
         vendor: Linksys, A Division of Cisco Systems
         physical id: 1
         bus info: pci@07:00.0
         version: 00
         width: 32 bits
         clock: 33MHz
         capabilities: cap_list
         resources: iomemory:f6000800-f600081f iomemory:f6000000-f60007ff irq:11
```

Any help with this would be great. I want to get the wireless back up.

---

### Post by ozorba on 2006-11-23
Check that pcmcia recognised your card by executing the following command

pccardctl status

If you cannot see your card remove and insert it again. Then execute the following command:

dmesg

the last few lines should tell you if your card is recognised by the kernel.

If everthing fails try installing ndiswrapper that allows you to install the windows driver.

--
OZ

---

### Post by FrodoB on 2006-11-23
According to several folks on the web ndiwrapper is the only way. Both of these gents give links to NDIS files that worked for them:

[http://oasis.dit.upm.es/~jantonio/personal/aspire1410/](http://oasis.dit.upm.es/~jantonio/personal/aspire1410/)

[http://blog.felisberto.net/linux-on-the-targa-traveller-m32/](http://blog.felisberto.net/linux-on-the-targa-traveller-m32/)


Not much of an expert on ndiswrapper, but give it a try and maybe someone can jump in if you have issues.

---

