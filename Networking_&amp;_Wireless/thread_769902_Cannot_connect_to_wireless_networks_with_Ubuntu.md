---
title: "Cannot connect to wireless networks with Ubuntu"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by johnnyboyc on 2008-04-26
My laptop (currently running Hardy) cannot detect ANY wireless networks. This is all the information I have.

lspci gives:

```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

and lshw -C network gives:
```

  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1a:bc:67
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.67 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0


```

also, iwconfig gives:
```


lo        no wireless extensions.

eth0      no wireless extensions.
```

and iwlistscan gives:
```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

Please help me, I have no clue what's going on here. 

Thanks a million, 
John

---

### Post by imakeart on 2008-04-27
Hi John,

Don't know if you've found a solution or not yet, but you might want to try my solution. I too have an Atheros Wireless Card and it showed up in lspci but just didn't work.

You will need to find the drivers for you wireless card model - which you can usually do on Google.

Then take a look at this post: 
[http://ubuntuforums.org/showthread.php?p=4791552#post4791552](http://ubuntuforums.org/showthread.php?p=4791552#post4791552)

I'm told this won't work for everybody, but its worth a try I guess.

---

### Post by johnnyboyc on 2008-04-27
Thank you so much for your help, but sadly I still have the same problem :(

I still cannot see any wireless networks in the network manager.
Any other suggestions?

Thank you!

---

### Post by johnnyboyc on 2008-04-27
So now after following the above advice, I am 99.99% sure that the drivers are all set. So if it isn't a driver problem, what can it be?
Thanks for all the considerations and advice, I've been struggling with this problem since 7.04.

---

### Post by johnnyboyc on 2008-04-27
More updates:
My wireless works perfectly in Windows vista (i'm dual booting) and  when I hook my laptop up to the internet via ethernet cable, it works fine in Ubuntu.

I had this exact same problem in Ubuntu 7.04, and 7.10 and it still  is unresolved in 8.04. 

I have been struggling with this for days, can someone offer a suggestion?

Thanks so much again.

---

