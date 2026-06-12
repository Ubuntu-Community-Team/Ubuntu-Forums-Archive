---
title: "Wireless Interface Disappeared"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by wacko_cracko on 2008-02-15
Hi

I hada bunch of updates outstanding which i went and installed, during the day i also added some bluetooth package management apps from synaptics, later in the evening tried to start my laptop at home but no wireless! checked to make sure the wireless was on and yes it was (the bluetooth wireless etc are all through one switch!) the light doesnt come on etc, tried to restart networking etc, but it wasnt even seeing the interface (my wireless runs on eth1) .. I have a Dell D420

tried a few different things

```
lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:d4:ef:c7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5752-v3.19 ip=10.144.45.52 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s"
```

It also definately see's the hardware 

```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1021
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
```

The sound also stopped working yesterday when i try the volume bar i get the following
> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured."

I have gstreamer plugins and codecs installed so dunno why its doing this! for some reason i also seem to be running the server version as far as i rememver i did not install this

uname -a

> Linux bubli 2.6.22-14-server #1 SMP Tue Feb 12 08:27:05 UTC 2008 i686 GNU/Linux

Could this be the issue, the only other install is the generic one, this all started yesterday, when i first installed ubuntu everything worked out of the box so not sure where i have gone wrong!

Any help appreciated!!

---

### Post by fbuchele on 2008-02-15
for the wireless post ```
 sudo iwconfig
```

As for anything else, i'm not quite sure on that, maybe you should try a different forum?

---

### Post by deedeesuzanne on 2008-04-01
I think I have the same problem. Did this ever get fixed for you? My eth1 wireless interface disappeared some weeks ago, and I haven't yet found an answer. My lshw -C network output is the same except it doesn't say network UNCLAIMED, just "network."

I had assumed the problem came from a package update and re-boot, but I've since re-installed and upgraded my system and still no dice.

Any help much appreciated!

---

