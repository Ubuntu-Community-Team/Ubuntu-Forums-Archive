---
title: "Marvell WiFi troubleshooting -- easier steps, please!"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by digitig on 2008-10-27
Ok, trying again with Ubuntu after a couple of years. I'm still hitting the problem that it won't recognise my WiFi card. Judging from what MS WIndows tells me, it's a "Marvell Libertas 802.11 b/g Wireless" card.

Working through the HowTo at [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking), I find that the card isn't listed under System-->Administration-->Networking, so I go to [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).

The first step of that HowTo is to "To check if device is recognized use the lshw command". I don't know how to use the lshw command to check if the device is recognised! I mean, I can type "lshw" into a console, then after seeing the message that I should have done it as a super user I can type "sudo lshw", and I get a few screenfulls of information that doesn't mean much to me at all. Third time lucky: "sudo lshw | less". I see:
        *-network:1
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: c
             bus info: pci@0000:05:0c.0
             logical name: eth1
             version: 13
             serial: 00:15:f2:1e:44:7f
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair

Is that my WiFi, or is it my wired ethernet? The bus looks right (MS Windows said "PCI Slot 3 (PCI) bus 5 device 8 function 0", and lshw says "bus info: pci@0000:05:0c.0". I have no idea how to read that, but it has a 5 in it! On the other hand, it seems to say the logical name is eth1, and System-->Administration-->Networking says eth1 is a wired network card.

Looking for help on my specific card on the web, I found the suggestion to try lspci -v, and find:
        05:08.0 Ethernet controller: Marvell Technology Group Ltd.
        Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: ASUSTeK Computer Inc. Unknown device 138f
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at d9000000 (32-bit, non-prefetchable) [size=64K]
        Memory at d9010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
The 802.11 in that looks like WiFi to me.

Is there a WiFi HowTo for *non*-gurus? If not, could somebody tell me if what I've found means that I can confidently check off step 1 in the troubleshooting HowTo? And then guide me *gently* through the next steps?

Thanks in advance!

---

### Post by caljohnsmith on 2008-10-27
> **digitig said:**
> 
```
        05:08.0 Ethernet controller: Marvell Technology Group Ltd.
        Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: ASUSTeK Computer Inc. Unknown device 138f
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at d9000000 (32-bit, non-prefetchable) [size=64K]
        Memory at d9010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
The 802.11 in that looks like WiFi to me.
```

Yes, that's your wireless card, and it looks like your wireless chipset is Marvell W8300. So the trick will be finding Windows drivers for your card, and then you can use "ndiswrapper" to install the drivers in Ubuntu. Are you using 32 bit or 64 bit Ubuntu? If you are using 64 bit Ubuntu, you will have to find 64 bit wireless drivers. Do you have a CD that came with your wireless card? That should have the wireless drivers on it. Just look for the Win XP (not Vista) drivers on the CD; you will need two files, the .inf and .sys files. Or you can go to the manufacturer's website and download the latest drivers. Once you get the drivers, I can help you install it with ndiswrapper if you want. :)

---

