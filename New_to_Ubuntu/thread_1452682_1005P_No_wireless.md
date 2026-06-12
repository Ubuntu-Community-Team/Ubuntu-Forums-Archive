---
title: "1005P No wireless"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by 317070 on 2010-04-12
I got myself a new "Asus eee 1005P" notebook, downloaded and installed Win7Starter, TinyXP, Tiny7 and the ubuntu netbook remix (9.10 I believe): Everything works great, but I don't have wireless on Ubuntu! Since this is a netbook, _that's_ annoying.

I have tried to follow the wiki: ( [http://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus](http://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus) Eee PC )

But after installing the XP-driver (which worked on TinyXP) ndisgtk says: "unable to see if hardware is present" with a red exclamation mark. after which it said "Hardware present". 
But still, no wireless.

I uninstalled the driver again, and now "sudo lshw -c network" reads:
>   *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f8000000-f800ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:5f:af:35
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
Any ideas/information on how to solve this issue???

Edit @ADMIN: might have been the wrong place to ask, could you move this to [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) ?

---

### Post by 317070 on 2010-04-12
Apparently, you need to LEFT-CLICK on the wireless Internet icon to select a wireless network.

Issue solved :lolflag:
Thank you for this troubleshooting guide: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

