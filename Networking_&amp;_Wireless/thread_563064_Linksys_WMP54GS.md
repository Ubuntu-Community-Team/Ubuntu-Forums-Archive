---
title: "Linksys WMP54GS"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by KLoWnTaZ on 2007-09-29
Ok I am Havin Trouble Getting This to work.

I Tried this [http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+broadcom)

However It hung in the installation. When It said Installing ndiswrapper whole system locked up. I haven't undone whatever it change because to be honest I have no Idea how.

So I am now completely confused on how to get it to work. Here is the info often requested with wireless problems.

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
02:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 08
       serial: 00:02:b3:99:66:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=206.74.179.87 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:feaff000-feafffff ioport:df00-df3f iomemory:fe900000-fe9fffff irq:18
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@02:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
       resources: iomemory:feafc000-feafdfff irq:10

All I can say is HELP :lolflag:

---

### Post by kevdog on 2007-09-29
Im somewhat familar with that thread.  Did you do any downloading of the source ndiswrapper files or do you know??  I just want to know since if not we can go through a manual installation of ndiswrapper, but this requires either you have a working internet connection (like a wired ethernet) or a different computer with internet connection with usb stick for file transfer along with the installation disk.

---

### Post by KLoWnTaZ on 2007-09-29
I downloaded the files  (I Think) However I have the wired connection ran to this comp for the moment. So lead me through what is needed I am all ears. However I am a newbie so I make errors easily. :lolflag:

---

### Post by KLoWnTaZ on 2007-09-29
Downloaded ndiswrapper-1.48. however I have no Idea how to install it :roll: some days I jus don't got it :P

---

### Post by KLoWnTaZ on 2007-09-29
Bump

---

### Post by pickles46 on 2007-10-27
I think once you get the package onto ubuntu (desktop), you start up synaptic and select "open a downloaded package"  or something along those lines. Then the package details will be added to the list of packages, search or find "ndis" files on the there there will be two; one for the kernel update and one to install the ndis. Right click both and select "mark for installation". click apply at the top and have your ubuntu install disc ready.

Please take note I am pretty new to linux so don't quote me on it but I think I have the basic concept down.

But I have an issue with this myself, my primary cd rom drive is broken so I use an external one to load everything but when it asks me to insert the install disc it only searches the broken cd drive for the information that's on the external source. I know that in the "drives" section it's labeled "cd rom 1" and I can see that it is functioning properly yet it is not selected as my primary drive.

So I guess my real question is, how do I mark a certain cd rom drive as the primary drive and is it just a synaptic setting or a system setting?

Any help would be greatly appreciated. :)

---

