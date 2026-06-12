---
title: "Unable to connect to internet"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by Somelier on 2015-03-17
Hallo!
I installed ubuntu 14.04 yesterday to my laptop. I am a brand new ubuntu user, not really experienced in programing or whatsoever.

I am trying hard to get my internet working but I just cannot do it by myself. Wifi wont work at all, since i probably miss the correct driver.

Connection to my router via ethernet is working, in network center I can see that I am connected to my network, but I still cannot open any website.

I can also connect to other computer via ethernet cable, I can share files, but I cannot share internet connection.

ifconfing -a gives back this:

```
eth0 
Link encap:Ethernet HWaddr 00:1d:09:3e:5c:f3
inet addr:10.42.0.1 Bcast:10.42.0.255 Mask:255.255.255.0
inet6 addr: fe80::21d:9ff:fe3e:5cf3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:169 errors:0 dropped:0 overruns:0 frame:0
TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:19332 (19.3 KB) TX bytes:35104 (35.1 KB)
Interrupt:16


lo 
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:609 errors:0 dropped:0 overruns:0 frame:0
TX packets:609 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:46441 (46.4 KB) TX bytes:46441 (46.4 KB)


wlan1 
Link encap:Ethernet HWaddr 00:00:4a:01:00:00
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

and lspci gives:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev
0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev
0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev
02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev
02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev
02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev
02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev
02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev
02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev
02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev
02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller
[AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev
22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet
Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

```

thanks for your help!

---

### Post by TheFu on 2015-03-17
It is most likely a DNS issue.
Can you **ping 8.8.8.8**?
What does **dig google** return?

I bet the IP works, but the nameserver lookup doesn't. If that is true, it is just a DNS issue, so check those settings and if your home router is providing DHCP (IP and DNS), they could be something funny happening there. Unlikely, but ..

---

### Post by Bucky Ball on 2015-03-17
Welcome. Coincidentally,[ fixed one of these up just today]("http://ubuntuforums.org/showthread.php?t=2269595&p=13246933&viewfull=1#post13246933") for another user, same card but slightly different issue. Hopefully yours will be as easy. Please give the output of this command which will tell us what driver you have installed currently:

```
sudo lshw -C network
```

If it isn't what I think it might be, TheFu may be on the money with the DNS being amiss at either the router end or in how you have the wireless configured locally.

Have you done anything so far to try and get the wireless up? Installed anything? Tweaked any settings?

---

### Post by Somelier on 2015-03-17
Ubuntu souls!
Good to hear from you!

Unfortunately I dont know what DNS is or how to fix the roblem :P I know how to get to my router, and I found some DNS field there, but it is empty. Here is a creenshot of what I mean. (My router firmware has only slovak localization, sorry...)

[IMG]http://i58.tinypic.com/2199pjn.png[/IMG]

**ping 8.8.8.8 **returns:
```
connect: Network is unreachable
```

and **dig google **returns:
```
; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> google;; global options: +cmd
;; connection timed out; no servers could be reached
```



sudo lshw -C network returns:
```
*-networkdescription: Ethernet interface
product: 88E8040 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 12
serial: 00:1d:09:3e:5c:f3
size: 100Mbit/s
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt
100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full
ip=10.42.0.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:44 memory:f9ffc000-f9ffffff ioport:de00(size=256)
*-network
description: Network controller
product: BCM4321 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 03
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f9efc000-f9efffff memory:f0000000-f00fffff
*-network
description: Wireless interface
physical id: 2
logical name: wlan1
serial: 00:00:4a:01:00:00
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=3.16.0-30-generic firmware=666.2
link=no multicast=yes wireless=IEEE 802.11bg
```


I unfortunately installed b43 driver which is not a good one for my card :/ I dont know how to get rid of it now...

---

### Post by TheFu on 2015-03-17
Looks like the router connection from the router to the internet isn't working.  So ... the problem is between the computer and the router. Let's forget about wifi - getting that to work can be very difficult, though most of the time, it just works these days.

Things to check:
* ethernet card driver - yours is using a sky2 driver; are there known issues with your network chips and that driver?
* ethernet card port - this is a physical check
* ethernet cable - is it "good" - try a different cable.
* router port - try a different port
* router isn't working - try to reboot it.
* DSL/DOCSIS modem - try to reboot it.  

If other devices can get to the internet then most of the router seems to be working. Swap the ethernet port connection between the working and non-working router plugs. What happened?

Also - try to ping the router IP from the computer.  That will tell us if it is a LAN issue or not. If the computer can ping the router, there are 2 logical issues to check - routing and DNS.

---

### Post by Bucky Ball on 2015-03-17
Yep, also wrong driver for the BCM4321. Run the instructions I gave in the [previous link ]("http://ubuntuforums.org/showthread.php?t=2269595&p=13246933&viewfull=1#post13246933")and that should get you a solid wireless connection ... on the BCM4321 device that is. I have no idea what this is:

```
*-network
description: Wireless interface
physical id: 2
logical name: wlan1
serial: 00:00:4a:01:00:00
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=3.16.0-30-generic firmware=666.2
link=no multicast=yes wireless=IEEE 802.11bg
```

If it is a wireless dongle, take it out, reboot and run the code I provide in the link above and see if you still have an issue. Part of your problem could be that you have two wireless devices in the box. Please explain which one is a USB device, if it is, and take it out, reboot, and run 'sudo lshw -C network' again so we can see what's going on with the internal device. :-k

This:

```
*-network
description: Network controller
product: BCM4321 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 03
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: **driver=b43-pci-bridge** latency=0
resources: irq:17 memory:f9efc000-f9efffff memory:f0000000-f00fffff
*-network
```

... on the other hand, generally runs fine 'out of the box', but in this case, wrong driver. The code I suggest will get the right driver in there.

---

