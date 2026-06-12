---
title: "Compaq V3118AU with Broadcom Chipset 4311 - Help Required"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by ozPATT on 2007-03-01
Hi All, 

I am now in desperate need of help... Following the relatively recent update taking the kernel to -11 from -10, as a lot of other people seem to have experience, I have lost my wireless card...

> SIOCGIFFLAGS error: No such device

I have scanned these forums and attempted a lot of the suggestions, but still no joy. Infact, much less joy than I had, because I used to be able to boot -10 so that I could still use my internet wirelessly. Feeling brave and with a couple of hours spare this afternoon - about 3 hours ago - I decided to tackle the problem. Now unfortunately I have no wireless on either kernel...

So... here is various output, I am pretty new to this kind of thing, so I would really appreciate some help...

```
patrick@localhost:~$ ndiswrapper -l
bcmwl5 : driver installed
```

```
patrick@localhost:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

```
patrick@localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

```
patrick@localhost:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
```

```
patrick@localhost:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:0C:FB:39  
          inet addr:192.168.1.10  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe0c:fb39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:743793 (726.3 KiB)  TX bytes:111182 (108.5 KiB)
          Interrupt:209 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KiB)  TX bytes:5276 (5.1 KiB)
```

```
patrick@localhost:~$ lspci | grep Broadcom\ Corporation
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
```

```
patrick@localhost:~$ sudo ifup eth1
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```

```
patrick@localhost:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:c3000000-c3003fff irq:10
```

```
patrick@localhost:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
patrick@localhost:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed 
patrick@localhost:~$ sudo rmmod ndiswrapper
patrick@localhost:~$ sudo modprobe ndiswrapper
```

If any other information is required, please let me know. Again, I would really appreciate help with this

Many Thanks

Patrick

---

### Post by Kobalt on 2007-03-01
Hello,

I have the exact same card and I got it to work pretty easily, I helped out someone with the same card here, you should follow the instructions and you should be done : 
[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

Cheerio !

---

