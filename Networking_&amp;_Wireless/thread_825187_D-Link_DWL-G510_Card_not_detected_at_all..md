---
title: "D-Link DWL-G510 Card not detected at all."
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by ArrowApollo on 2008-06-10
I just installed xubuntu on an old gateway with a newish d-link wireless pci card in it. However it doesnt detect the card at all. The network options dont even give me wireless as a choice. When I type if config into the terminal only eth0 and lo show up. and when I type lshw -C network, network: 1 is listed as UNCLAIMED.

I downloaded the driver and used ndiswrapper just to see if maybe something would happen, but even though the driver installed alright it says no hardware detected.

Any help?

---

### Post by ArrowApollo on 2008-06-10
I've been searching around to see what to do and I wen to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and typed in lspci -v | less to see what i would get from the wireless card and this is what it said:

00:10.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 1aa6 (rev 07)
        Subsystem: D-Link System Inc Unknown device 3a09
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 9
        Memory at 20050000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Memory at 20060000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

I don't know what it all means but maybe it'll help someone help me.

---

### Post by ArrowApollo on 2008-06-10
So I went on a bit more and looked at 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

and it says to use the madwifi driver but I looked at madwifi before and didnt know what to do. I also don't know what revision the card is.

---

### Post by chili555 on 2008-06-10
Well, the *Supported Cards* link suggests this is an Atheros chipset, not the marvelous Marvell. This:> Ethernet controller: Marvell Technology Group Ltd.is a bit confusing, because it refers to ethernet, but says D-link. Let's try to be sure with:```
sudo lshw -C network
```I think it will probably turn out to be an Atheros, so drop your install CD in the tray, open System-Admin-Synaptic. Go to Tools-Repositories and enable the CD as an installation source. Press Reload and search for *linux-restricted-modules* and install it if it's not already there. It contains the madwifi drivers for Atheros cards.

Post back and we'll proceed.

---

### Post by ArrowApollo on 2008-06-10
brian@brian-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 25
       serial: 00:80:c6:ec:b6:61
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.2.2 latency=66 maxlatency=56 mingnt=8 module=tulip multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64

---

### Post by ArrowApollo on 2008-06-10
I took the case off to make sure its G510 and not 510 since it still says marvell, and it's definitely G510.

---

### Post by chili555 on 2008-06-10
If you look here: [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)  you will see the D-link DWL-G510 has had no less than **four** different chipsets! Only one, Rev. 07, shows with a Marvell chipset. Then there is this:> 802.11g 	 DWL-G510 rev. 07 	 	 PCI 	 Marvell 	 W8300 	 green  	 Part of kernel, thanks to the OLPC project Part of the kernel? How come it didn't load automagically? W8300? I don't find that driver in my fully-updated system. ??? The OLPC project? One Laptop per Child?

The more I read, the less I know. The search goes on.

---

### Post by ArrowApollo on 2008-06-10
Wow, that so unexpected. Holy cow. Should I reinstall and see if it shows up? O, and I forget to say that I lost the antenna that screws into the back of the card that comes out of the slot. But that shouldn't matter in detected the card right?

---

### Post by ArrowApollo on 2008-06-10
I was searching and found some threads, maybe they'll help you too.

[http://ubuntuforums.org/showthread.php?t=654940](http://ubuntuforums.org/showthread.php?t=654940)

[http://ubuntuforums.org/showthread.php?t=140330](http://ubuntuforums.org/showthread.php?t=140330)

[http://ubuntuforums.org/showpost.php?p=1389774&postcount=11](http://ubuntuforums.org/showpost.php?p=1389774&postcount=11)  <----I tryed to find the file mentioned here and do this solution but it wasn't there.

[http://ubuntuforums.org/archive/index.php/t-171859.html](http://ubuntuforums.org/archive/index.php/t-171859.html)  <--this guy just pulled out all his PCI cards, and put them back in reorderd, and it workd.

[http://madwifi.org/wiki/Compatibility/D-Link#DWL-G510](http://madwifi.org/wiki/Compatibility/D-Link#DWL-G510) <----and this says there are no open souce drivers :(.

I'm just gunno try different drivers with ndiswrapper until you have an idea for something else i can do.

---

### Post by ArrowApollo on 2008-06-11
So I shuffled the PCI cards and I'm trying different drivers and the one I just put in says the hardware was detected and I'm trying to establish a connection right now!

This driver worked!

[http://www.driverstock.com/D-Link-DWL-G510-driver-download/24-28-11277-86654/index.html](http://www.driverstock.com/D-Link-DWL-G510-driver-download/24-28-11277-86654/index.html)

Odd cuz I tried it before. I guess shuffling the cards did it!

Thank for the help though!

---

