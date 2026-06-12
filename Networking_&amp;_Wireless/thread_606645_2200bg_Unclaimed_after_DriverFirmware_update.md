---
title: "2200bg Unclaimed after Driver/Firmware update"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by scottsee on 2007-11-08
I've been searching for hours and hours to fix this problem.  I was following the instructions on how to update my iwp2200 drivers to allow for packet injections from the how-to Ubuntu[*here*](http://ubuntuforums.org/showthread.php?t=501148&highlight=2200+patch).  I couldn't get the 1pw2200 to show they had been update after to installing and patching for 1.2.1 (dmesg | grep ipw would showed 1.2.0). So I tried to updating everything to the newest firmware, dirver, patches available using [*this*](http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/) guide intended for the Gutsy 7.10 distro.  I didn't think it would matter because it is for the same harware, but following those steps and rebooting I'm not anable to get my 2200BG wireless back up and running!  Here is what I am getting..  Any pointers are apricated!

lshw -C network
```
  *-network:0 DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a3:4c:e6
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 latency=64 link=no multicast=yes port=twisted pair
       resources: iomemory:dfbfe000-dfbfffff irq:18
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
       resources: iomemory:dfbfd000-dfbfdfff irq:10

```

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
02:01.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
02:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
02:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

```

sudo modprobe ipw2200 debug=15 
```
Fatal: Error inserting ipw2200 (/lin/modules/2.6.20-16-generik/kernel/drivers/net/wireless/ipw2200.ko):  Unknown symbol in module, or unkown parameter (see dmeseg)

```

Iwconif comes back as "Lo" & "eth0" :  No wirelwss extensions
Ifconfig only lists "lo" as a : Local Loopback.  

I've tried installing the older drivers (ipw2200-1.2.1 & ieee80211-1.2.17) hopeing it would correct the problem but when I check to see if they have been installed correctly I get the following..  

dmesg | grep ipw
```

[       18.400000]  ipw220: unknown parameter 'rtap_inface'
[   801.1840000]  ipw220: unknown parameter 'rtap_inface'
[ 1184.2840000] ipw220: unknown parameter 'rtap_inface'
[ 3003.1040000] ipw220: unknown parameter 'rtap_inface'
[ 3009.8280000] ipw220: unknown parameter 'rtap_inface'
```

dmesg | grep ieee comes back with the updated dirver info " 802.11 data/management/conrol stack, 1.2.17"  
  
It looks to me that I have chaged somthing that points to the driver, or just flat deleted it somehow..??..?.  Is there a roolback driver option in Ubuntu Fawn?  
Can someone PLEASEEEE shed some light on what is going on here and what I can do?   I've been up All night trying to figure this out and I'm stumped.  Thanks!

Scott 
[email]Scottsee@hotmail.com[/email]

---

### Post by scottsee on 2007-11-08
...

---

