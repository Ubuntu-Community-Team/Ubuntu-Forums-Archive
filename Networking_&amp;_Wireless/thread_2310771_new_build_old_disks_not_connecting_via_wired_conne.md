---
title: "new build old disks not connecting via wired connection"
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by Fsirett on 2016-01-21
First, I am using a new Gigabyte ga-f2a88xm-d3h motherboard with a new AMD a10 7850 chip. The hard drives (3) came from my old computer and I do have the legacy Ubuntu (15.10) running and it seems to be running well.

My internet is directly wired in and does not connect, although there are other devices in the house that are running wifi perfectly well from the same router.

Prior to the decline and fall of my old computer the internet connection also ran perfectly well. It is the new system that is failing to connect. 

I am certain this is nothing very complex, probably something dumb that I did or did not do. Therefore I hasten to add that I DID turn on the IOMMU(?) in the bios that I see caused so many problems to so many.

I also include 

lspci Output:

 ```
00:00.0 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor RootComplex00:00.2 IOMMU: Advanced Micro Devices,Inc. [AMD] Family 15h (Models 30h-3fh) I/O Memory Management Unit
00:01.0 VGA compatible controller:Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]
00:01.1 Audio device: Advanced MicroDevices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
00:02.0 Host bridge: Advanced MicroDevices, Inc. [AMD] Device 1424
00:03.0 Host bridge: Advanced MicroDevices, Inc. [AMD] Device 1424
00:03.1 PCI bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port
00:04.0 Host bridge: Advanced MicroDevices, Inc. [AMD] Device 1424
00:10.0 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced MicroDevices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices,Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced MicroDevices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced MicroDevices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced MicroDevices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced MicroDevices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0
00:18.1 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1
00:18.2 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 2
00:18.3 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 3
00:18.4 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 4
00:18.5 Host bridge: Advanced MicroDevices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 5
01:00.0 Ethernet controller: RealtekSemiconductor Co., Ltd. RTL8111/8168/8411 PCI Express GigabitEthernet Controller (rev 0c)



```

And I also have the ifconfig

ifconfig Output:

```
enp1s0    Link encap:Ethernet  HWaddr40:8d:5c:7d:c4:1e          UP BROADCAST RUNNINGMULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0dropped:0 overruns:0 frame:0
          TX packets:131 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1104 (1.1 KB)  TXbytes:19441 (19.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128Scope:Host
          UP LOOPBACK RUNNING MTU:65536  Metric:1
          RX packets:1401 errors:0dropped:0 overruns:0 frame:0
          TX packets:1401 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
RX bytes:128461 (128.4 KB) TX bytes:128461 (128.4 KB)
```

From what my limited understanding tells me, I apparently have a working system that is being blocked on it's way to the router and it is, if I may exaggerate, a laughably simple process to unblock it. Unfortunately I have a rather severe block where my brain should reside and A
I am not at all certain what to do about all this. Plenty online for wireless problems, but not much for we Neanderthals that still insist on wired connections, desktop computers, grammar and telephones that are actually good, and easy at making telephone calls!

I thank you all, once again, for your kind indulgence. My blessings will go far ro offsetting the curses coming from my local repair shop.

Frank Sirett

---

### Post by Fsirett on 2016-01-23
Did I mention I was stupid? If not I am now accepting that exalted title.

I tried running a live disk on the new machine but it did not work nor did an old USB version. My immediate assumption was that it had something to do with my build and I did not have enough time on an alternate computer to burn a new one. I have now had a chance to build a new live USB and, with great joy, It connects to my internet! I also had the chance to use GParted that seems to have disappeared from my disks, and I have found some problems on one of my drives. Hence (I assume!) the problem with disappearing GParted and no internet connection, even though the browsers would load as if normal.

I am now going to partition my new drive and put the operating system on one partition and use a second partition for my /home folder so I can replace the OS at will. I think I did this with the old system, but I shall do it again and replace the new /home files with the old ones and see if things work that way.

Moral: do not trust old Live media to be operating correctly; they seem to have an expiry date, at least mine do. Lesson learned (another) for a very backward scholar
I hope this helps one with similar problems

Cheers for all your efforts!

Frank Sirett

---

