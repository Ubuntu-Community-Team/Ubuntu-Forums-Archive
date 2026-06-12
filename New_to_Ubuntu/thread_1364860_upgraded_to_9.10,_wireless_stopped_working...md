---
title: "upgraded to 9.10, wireless stopped working.."
date: 2009-12-26
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2009-12-26
Ok so.. I've recently reinstalled Ubuntu onto my laptop. I installed 9.04 first and the wireless worked flawlessly.. I then upgraded to 9.10 as prompted and now my wireless isn't working, and the nm-applet isn't running when told to.

Here's the output of lshw -C network: 

```
 
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:17:27:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.3 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:f0101000-f0101fff ioport:2000(size=64)

```

Any help appreciated, thanks!

---

### Post by bkratz on 2009-12-26
> **MrJoeyUK said:**
> Ok so.. I've recently reinstalled Ubuntu onto my laptop. I installed 9.04 first and the wireless worked flawlessly.. I then upgraded to 9.10 as prompted and now my wireless isn't working, and the nm-applet isn't running when told to.

Here's the output of lshw -C network: 

```
 
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:17:27:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.3 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:f0101000-f0101fff ioport:2000(size=64)

```

Any help appreciated, thanks!

There is no driver associated Look at this thread

[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)

---

### Post by theozzlives on 2009-12-26
When I went from 9.04 to 9.10, I had to be "wired" and then activate the drivers for my wireless to work. Using the Broadcom STA driver and it works great now.

---

### Post by MrJoeyUK on 2009-12-26
That thread didn't really help, but I did take a look in hardware drivers and found this:

[img]http://img706.imageshack.us/img706/8937/screenshothardwaredrive.png[/img]

I've followed two guides on how to activate it, but they both didn't work, as most terminal commands returned results saying I already had this installed etc.

---

### Post by MrJoeyUK on 2009-12-26
No problem fellas, I found a 3rd guide which made it work. Thanks for the help!

---

### Post by bkratz on 2009-12-26
> **MrJoeyUK said:**
> No problem fellas, I found a 3rd guide which made it work. Thanks for the help!

What guide did you find that helped? and please go to thread tools and mark solved so it can easily be found again by someone else.


Sorry I just reloaded and noticed that you marked it solved, thanks

---

