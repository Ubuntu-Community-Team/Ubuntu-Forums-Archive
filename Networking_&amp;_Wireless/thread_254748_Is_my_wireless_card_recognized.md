---
title: "Is my wireless card recognized?"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by Skia_42 on 2006-09-10
I have a new Gateway Tablet PC and I need to ge the wireless card working. Wireless Internet was working under MS XP and now I am trying to get it to work under 6.06. I have been following the [wirless troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") in getting it to work and I have a question. The output of sudo lshw -C network gives me the following:
> skye@skye-laptop:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:ae:ff:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e1000 driverversion=7.0.33-k2 duplex=half firmware=0.5-1 ip=192.168.1.7 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d4000000-d401ffff ioport:2000-201f irq:58
  *-network
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:d6000000-d6000fff irq:169

Is the Network Controller my Wireless card or something else? I am not sure what to do from here on.

---

### Post by lukew on 2006-09-10
You got two network cards. One is a gigabit :o and requires a wire and the other is an onboard intel wireless.

Luke

---

### Post by Skia_42 on 2006-09-10
So the second part is my wireless which is built into the motherboard? I am assuming that this means that the driver is working then... > configuration: driver=ipw3945
What do I need to do to get it working?

---

### Post by lukew on 2006-09-12
I presume it is one of those onboard intel wifi nics.

nsdwrapper; see the wiki there are quite a few dedicated pages for each card. Normally it just involves downloading the windows driver for you card; download nsdwrapper and pairing the two together!

Luke

---

