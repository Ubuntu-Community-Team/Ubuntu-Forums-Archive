---
title: "Wireless not working in Ubuntu 9.04"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by robbiechad on 2009-06-19
Hello all, I have just loaded the new Ubuntu 9.04, evrything seems to work OK except for the. wireless connection for my laptop. It looks like Ubuntu can't see the wireless card. I am a newbie so am not very good on the terminal side of inputting commands ... not a clue.I did however download    the new edition of Fedora 11 two days ago and tried that out as a live CD. I was pleasantly surprised to find that everything worked straight out of the box so to speak Wireless operation worked first time all I had to do was put in the password for my wireless connection. I would like to get my Ubuntu wireless working as I hate Vista.  Linux  promises to do everything I need it to do, the only decision is which distro is right for me? Many thanks in advance..

---

### Post by ptn107 on 2009-06-19
What kind of laptop?  What kind of wireless card?

---

### Post by robbiechad on 2009-06-19
Hi, Sorry about that its a Sony Vaio laptop with an Atheros Wireless card. I looked at another post on wireless and put in the command to check what it said this is what I got :

*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:f3:b8:f5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:3b:29:7a:52:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
:lolflag:Hope this helps clarify some details  Regards Rob

---

### Post by Sealbhach on 2009-06-19
Hi, you need the madwifi driver, it looks like it needs to be compiled. Have a look at this guide here:

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

which is referred to in this forum thread here:

[http://ubuntuforums.org/showthread.php?t=1142160](http://ubuntuforums.org/showthread.php?t=1142160)

.

---

### Post by carml on 2009-06-19
If your card is an Atheros,probably the model you get under Ubuntu is wrong.
If you have got a Windows OS,can you please tell us from Control Panel->System->Perypherals Management (I suppose it's named so,mine is in Italian:) ) or by an other way the exact model of your wireless card?

---

