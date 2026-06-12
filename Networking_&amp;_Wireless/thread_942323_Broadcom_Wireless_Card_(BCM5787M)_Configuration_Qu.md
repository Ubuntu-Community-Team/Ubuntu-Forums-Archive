---
title: "Broadcom Wireless Card (BCM5787M?) Configuration Questions"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by lorenbr on 2008-10-09
I bought a new Acer laptop here in Thailand, and am trying to run it as an exclusively Ubuntu machine.  I've had my hiccups (as I expected), but the tinkering process has been fun.  Now the only major remaining hurdle is getting the wireless up and working.

My situation is made more complicated because I don't have an easy way to test the wireless.  I've still got my old mac Powerbook, which I used to setup a computer-to-computer network, which I am using as my basis for believing that things aren't working.  I set up a network, but when I go to the "Edit Wireless Networks" option off the DoubleComputerIcon (can't recall exactly what it is called... "gnome network manager"?) in the upper left hand corner of my screen, no networks show up.

When I type in:

```
sudo lshw -C network
```

I get something about my wired ethernet adapter, which is working fine, and then the following concerning my wireless adapter:

```
wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:9d:04:fb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.1.10 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
```

At this point I've tried so many things that I only vaguely understood that I'm just sort of lost, and don't even really know how to retrace my steps.  Is there any reason the computer-to-computer network wouldn't show up?  If not, then where do I go from here?  

I've followed a couple versions of the guide spelled out here:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
But it still doesn't appear to be working

I've also read that the Broadcom wireless cards have been a problem for Ubuntu in the past, so I'm willing to accept failure if that's the ultimate answer, but I don't feel qualified to make that diagnosis.  I'd appreciate a little hand in figuring this out.  I'm happy to do some more legwork, but at the moment I'm feeling a bit lost as to where to go.  Of course, without any place to really use my wireless at the moment, this isn't a pressing concern, but I do want this to work for when I take my computer with me on a trip or something.

---

### Post by Ayuthia on 2008-10-09
> **lorenbr said:**
> 
When I type in:

```
sudo lshw -C network
```

I get something about my wired ethernet adapter, which is working fine, and then the following concerning my wireless adapter:

```
wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:9d:04:fb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.1.10 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
```


This is actually your wired card.  Do you have more information from lshw -C network?  Also, can you post the results of lspci -nn?  Thank you!

---

### Post by lorenbr on 2008-10-09
Haha!  I told you I was confused.

Entire line from lshw -C network

```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:ac:64:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:9d:04:fb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half firmware=5787m-v3.23 ip=192.168.1.10 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
```

That makes some sense because I was confused why my module kept coming up as tg3 and not "wl" or "nsdi[whatever-its-called]" which seemed to be the two options available.  I can now see it is "wl" which I remember being the one I didn't want.  But I thought I went through the fix for that already.  Anyways

lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
0a:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
0a:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
0a:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
0a:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
0a:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
```

Not sure why you're thanking me.  Thank you!

---

### Post by Ayuthia on 2008-10-09
You have one of the newer Broadcom cards (4312 rev 01 [14e4:4315]) which means that you can use the wl driver or the NDISwrapper driver.  The wl driver comes with Ubuntu so it should just be a matter of turning it on.  Have you tried enabling it through System->Adminstration->Hardware Drivers?  Make sure that the wl driver is enabled and that the Broadcom b43 driver is not.  The b43 driver currently does not support your card.

---

### Post by lorenbr on 2008-10-09
Well I guess that's all good then.  Is there anyway to verify the connection?  I still cannot find the network that I am supposedly setting up using the airport card on my PowerBook G4.  But I feel like that isn't indicative of anything.  On the Hardware Devices window off the System>Admin menu, wl shows up as checked, green dot, in use.  I suppose I may just have to sit on this till I get to a place with a verifiable WiFi connection.

Thanks again!

P.S. Ayuthia?  Like Ayutthia (or however they transliterate it) the ancient capital of Thailand?  Coincidence?

---

### Post by Ayuthia on 2008-10-09
> **lorenbr said:**
> Well I guess that's all good then.  Is there anyway to verify the connection?  I still cannot find the network that I am supposedly setting up using the airport card on my PowerBook G4.  But I feel like that isn't indicative of anything.  On the Hardware Devices window off the System>Admin menu, wl shows up as checked, green dot, in use.  I suppose I may just have to sit on this till I get to a place with a verifiable WiFi connection.
If you go into the Terminal, can you check and see if you get any results when you type:
```
sudo iwlist scan
```
Hopefully it will see the PowerBook.

> P.S. Ayuthia?  Like Ayutthia (or however they transliterate it) the ancient capital of Thailand?  Coincidence?I figured that you would notice that.  My parents were born in Thailand and moved to the United States almost 40 years ago.  I was born in the US.  Our last name is Israngkun Na Ayuthia but we shortened it to Ayuthia because it made things too complicated here.  Like you said, the spelling of Ayuthia was created to match the sound, but if it was written in Thai, it should match the spelling of the ancient capital.

---

### Post by dt_matthews on 2009-11-07
Hi folks

I saw this thread and was hoping some kind soul might assist with my wifi problems. I have 64bit Koala installed and wired connection is fine but I cannot get wireless working (have tried ndiswrapper with the window7 driver file I use on the dual boot win7).

Here my outputs - from my very limited (almost zero in fact) I Cant even see the wireless hardware??

the wifi chip is enabled in the bios and the light is on so the interface should be active but it seems to be doing a good job of hiding!)

Thanks for your help,
dan

----------------------------
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:5e:9c:32
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.09 ip=192.168.1.67 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:d0000000-d000ffff

-----------------------------
sudo lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)

------------------------------
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
-----------------------------

---

### Post by dt_matthews on 2009-11-07
p.s. I did post this yesterday [http://ubuntuforums.org/showthread.php?p=8260048](http://ubuntuforums.org/showthread.php?p=8260048) but thought this was a similar hardware issue and that therefore it might kill two birds with one stone!!!

---

