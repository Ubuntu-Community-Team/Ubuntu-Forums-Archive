---
title: "wifi loses internet but not network"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by patriot70 on 2014-08-24
WIFI is a Netgear N300 USB adapter. Will have internet access for a minute or two after startup, but then it drops. Still have IP address. Have been unable to find issue.
Here is some info
lspci
```
00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 RAID bus controller: NVIDIA Corporation MCP78S [GeForce 8200] SATA Controller (RAID mode) (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200] (rev a2)
06:00.0 Communication controller: Conexant Systems, Inc. Device 2f82

```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:22:15:3f:23:76
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:41 memory:fce7c000-fce7cfff ioport:c880(size=8) memory:fce7e400-fce7e4ff memory:fce7e000-fce7e00f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 28:c6:8e:61:3b:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.59+,08/26/2009, 5.10.79.30 ip=192.168.1.223 link=yes multicast=yes wireless=IEEE 802.11g

```

iwconfig
```
wlan1     IEEE 802.11g  ESSID:"ATT744_2GEXT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:FC:AF:87:05:EB   
          Bit Rate=78 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-27 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:43195   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

```

Any help would be greatly appreciated.

---

### Post by varunendra on 2014-08-25
As soon as I see these not-natively-supported-chips-that-require-ndiswrapper, I lose 80% of my hope even before starting the troubleshooting. So with the remaining 20% hope to determine and solve the issue, let's take a look at your wireless setup.

While the adapter is plugged in and working, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
If you have the option, it would be best to get it replaced with a model that is natively supported in Linux.

---

