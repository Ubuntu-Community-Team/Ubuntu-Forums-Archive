---
title: "Network Card lock-up"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by Norst on 2007-07-08
This seems to be more of a driver or maybe NIC interface issue but I'm hoping for some help.

During periods of high speed downloads (sustained 10-16mbps) my network card will lock up. It can be reset by simply unplugging the network cable and plugging it back in. 

I've come to the conclusion that it is on this one machine by doing the following:
-new DSL modem
-replaced network cable
-tried DSL modem in both Modem/Router mode and bridged mode (acts as a modem only) with my old linksys router
-Downloaded 3 full DVD ISO images on another box running ubuntu with no lock ups or errors

Now this issue does not manifest while downloading small or low speed files. I can make use of the web and have no problem, it is only during sustained high speed, large files that this happens.

The interface I'm using in the one built on to my motherboard (ASUS P5LD2) Marvell 88E8053 PCI-E Gb LAN controller. 

Is there anyway I can find out if this issue is hardware related or driver related?

Any help would be great, thank you.

---

### Post by Norst on 2007-07-08
ok it seems this is a known issue with the sky2 driver and this card interface. There are mentions of this being fixed but it would seem that is not the case for me. There is also mention of some other sky driver that does work well, but I lack knowledge at this time of how to change the driver for this device. I will read further and if I find a solution I will post back. Please feel free to offer any quick tips that may help me along the way.

Thanks

---

### Post by fredj on 2007-07-09
Open a terminal. Type 'lshw -class network' (without the quote marks) and post the result here
so that we can see which driver you are using.

---

### Post by Norst on 2007-07-09
I was using the Sky2 driver. I installed the yukon driver right from the marvell site and now all is working perfectly. This is quite a popular issue it would seem (the high load lock up on some chipsets with the sky2). The new driver shows as sk98lin.

Norst

---

### Post by marwooj on 2007-07-18
> **fredj said:**
> Open a terminal. Type 'lshw -class network' (without the quote marks) and post the result here
so that we can see which driver you are using.

 sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:4d:42:4a:00
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=10.0.29.152 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f8000000-f8003fff ioport:9000-90ff irq:16
 sky2 eth0: disabling interface
[  800.552468] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  804.961406] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  804.961422] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  804.961447] sky2 0000:03:00.0: v1.13 addr 0xf8000000 irq 16 Yukon-EC Ultra (0xb4) rev 3

---

