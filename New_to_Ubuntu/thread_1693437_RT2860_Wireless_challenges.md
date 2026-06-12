---
title: "RT2860 Wireless challenges"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Nebjeb on 2011-02-22
I'm having trouble connecting  to the Internet with my RaLink RT2860 wireless.  
 

 I've been going through the help troubleshooting guides I can find and just keep going around in circles.

I'm  picking up my wireless network, it waits a few minutes then comes up with authentication required by wireless network, and I'm certain that the key is correct. 

 I'm using the driver=ndiswrapper+rt2860
 

 I've set up the windows wireless drivers, I think, like it was suggested in the wireless troubleshooting guide.

 I'm using Wubi, hopefully that's not a problem.

 I'm very new at Ubuntu but I'm learning a lot and enjoying it, I just would like to get the wireless working.

---

### Post by cariboo on 2011-02-23
Is there a reason why you aren't using the driver provided by the kernel?

---

### Post by Nebjeb on 2011-02-23
I really am new at this.

I went through the wireless troubleshooting guide.

I did:
# 5.2.1.&#8194;Check that the device is on
# 5.2.2.&#8194;Check for device recognition

When it came to recognition I did

sudo lshw -C  network

and got:

[INDENT]*-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:71:bc:01:cb:a2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2860 driverversion=1.56+Ralink Technology, Corp.,01 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:19 memory:fd7f0000-fd7fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:76:ac:b6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.69 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbf8000-fdbfbfff memory:fdb00000-fdb1ffff

[/INDENT]There was no "CLAIMED, UNCLAIMED, ENABLED or DISABLED".

So like a silly noob, which I am, I didn't think to do things systematically. I just went to the next section: 
[INDENT]5.2.3.&#8195;Using Windows Wireless Drivers
[/INDENT]I did all that, figuring out how to install a driver was a challenge and I'm not sure how I actually did it now, sorry. 

I've tried following a few different tutorials on the forum for the RT2860 but I have always come to a section where I don't know what to do next. 

I'm now trying the suggestions at [http://ubuntuforums.org/showthread.php?t=1682710&highlight=RT2860](http://ubuntuforums.org/showthread.php?t=1682710&highlight=RT2860)

I'll see how I go. I'm am an absolute beginner so any tips to point me in the right directions would be great.

---

