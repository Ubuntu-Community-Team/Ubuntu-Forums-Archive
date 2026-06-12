---
title: "Semi Noob needs help with top dog driver for gateway laptop"
date: 2013-12-24
forum: Networking &amp; Wireless
---

### Post by olymallen75 on 2013-12-24
I have been taking a bunch of advise from a bunch of different sites and this is as close as i have gotten but i'm so far away...

The laptop finally recognizes the driver and is installed and every thing LOOKS good but still no wireless
when i do 
ndisgtk  and i go to configure network it tells me that it cant

any and all help would be greatly appreciated...

08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless (rev 03)
        Subsystem: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
        Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [5c] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [e0] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Gateway, Inc. Device 0566
        Flags: bus master, fast devsel, latency 0, IRQ 43
        I/O ports at a000 [size=256]
        Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 80400000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
        Capabilities: [60] Express Endpoint, MSI 00
        Capabilities: [84] Vendor Specific Information: Len=4c <?>
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [12c] Virtual Channel
        Capabilities: [148] Device Serial Number 00-00-00-00-10-ec-81-36
        Capabilities: [154] Power Budgeting <?>
        Kernel driver in use: r8169


root@dawns-laptop:~# ndiswrapper -r NetMW14x.inf
couldn't delete /etc/ndiswrapper/NetMW14x.inf: No such file or directory
root@dawns-laptop:~# ndisgtk 0.8.3-1


** (ndisgtk:5988): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed
root@dawns-laptop:~# ndiswrapper -l
netmw14x : driver installed
        device (11AB:2A08) present
root@dawns-laptop:~#

---

### Post by tfrue on 2013-12-24
Give this article a good read and see if it helps any:
[http://ubuntuforums.org/showthread.php?t=1816095](http://ubuntuforums.org/showthread.php?t=1816095)

---

### Post by Bucky Ball on 2013-12-24
Welcome. 

Yuk. Please give the output of this:

```

sudo lshw -C network
```

What possessed you to install and use ndiswrapper? That is a thing of the past virtually a relic and most how-tos are out of date and obsolete. Ndiswrapper can be a problematic nightmare and may block any attempt to get the right driver in. Although you may be one of the unlucky ones that still needs to wrestle with it as for a handful it is the only way.

---

### Post by olymallen75 on 2013-12-24
chris, if im looking at it right i think its the exact oppisite of my problem... my cable works my wireless does not but i finally got the driver installed right so it looks and everything else looks good (well better than it has) but still no wireless in the network manager

---

### Post by olymallen75 on 2013-12-24
bucky,

as for ndiswrapper that is all i could find on the net i have been trying to do this for 3 days now and my system finally rec the driver is installed properly but nothing in the network manager.

output

root@dawns-laptop:~# lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88W8362e [TopDog] 802.11a/b/g/n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0210000-f021ffff memory:f0200000-f020ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:50:8a:cf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.14 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:a000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff
root@dawns-laptop:~#

---

### Post by Bucky Ball on 2013-12-24
Well, your wireless is not showing there is any driver is installed for it and is also showing up as an ethernet controller. Should be a network controller. This might not be a big deal but the main issue is that, ndiswrapper or not, there is no driver installed for your wireless according to the above output. What convinces you there is one installed?

---

### Post by olymallen75 on 2013-12-25
Bucky,

I dont really know what im doing i am learning as i go
i will post my findings that i have never had before
it always says driver not installed properly or something else this is the only positive that i have gotten

root@dawns-laptop:~# ndiswrapper -l
**netmw14x : driver installed**
**        device (11AB:2A08) present**
root@dawns-laptop:~# 

i have never been this close

i was also wondering should i reinstall a 32bit version of the distro
i dont know how to find out but i think im running 64bit

---

### Post by Bucky Ball on 2013-12-25
> **olymallen75 said:**
> i was also wondering should i reinstall a 32bit version of the distro

No. To find out, type 'uname -a' in a terminal.

You might want to have a read of this:

[http://forums.linuxmint.com/viewtopic.php?p=690753&sid=60d2fdeab54cd9e769d1ff10adffa05a](http://forums.linuxmint.com/viewtopic.php?p=690753&sid=60d2fdeab54cd9e769d1ff10adffa05a)

... particularly Dark Corner's post and solution at about post #10. Seems you card is notoriously difficult to get going in Ubuntu and ndiswrapper, unfortunately, is the only way (extremely rare now). Ndiswrapper v1.57 doesn't seem to work with it but 1.58 does. You'll need to research this more.

Good luck (I'd be tempted to buy a $5 dongle with a more common wireless chipset myself, but you could get lucky here with some concerted effort).

---

