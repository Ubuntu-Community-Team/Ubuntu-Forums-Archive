---
title: "Ethernet only works through dock on new ubuntu 20.04 sysytem?"
date: 2020-12-16
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2020-12-16
Hello, I recently installed ubuntu 20.04 on an MSI GS66 Stealth, running kernel 5.4.0-53-generic.

The wifi is working fine, and the ethernet works when connected through my dell USB-C dock. But when connected through the native ethernet port, the network settings say "cable unplugged". The laptop is brand new, so I doubt it's a hardware issue. My guess is drivers, but I'm not sure.

When connected to the dock, and with ethernet plugged into the dock,

```
ifconfig -a
``` returns:

```
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:a7:d5:a9:db  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enx54bf643fb650: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.132  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:8801:c300:e95:a443:41b5:4b39:5dbd  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::251a:a2c3:dc8a:9a55  prefixlen 64  scopeid 0x20<link>
        inet6 2600:8801:c300:e95:8c36:6723:e162:aebc  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1052:a443:41b5:4b39:5dbd  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1052:26b1:28e4:56b0:7923  prefixlen 64  scopeid 0x0<global>
        ether 54:bf:64:3f:b6:50  txqueuelen 1000  (Ethernet)
        RX packets 214995  bytes 244974654 (244.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 143793  bytes 18382704 (18.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4886  bytes 504789 (504.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4886  bytes 504789 (504.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 9c:29:76:f1:c4:4e  txqueuelen 1000  (Ethernet)
        RX packets 51462  bytes 69424624 (69.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7388  bytes 1113036 (1.1 MB)
        TX errors 0  dropped 2 overruns 0  carrier 0  collisions 0


```, and 

```
lspci
``` returns:

```
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation 6th-9th Gen Core Processor PCIe Controller (x16) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.2 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #2
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #17 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 06b6 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Comet Lake LPC Controller
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2019/PC SN750 NVMe SSD
3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)
```

When disconnected from the dock, and with ethernet plugged directly into the ethernet port

```
ifconfig -a
``` returns:

```
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:a7:d5:a9:db  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5484  bytes 557651 (557.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5484  bytes 557651 (557.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 9c:29:76:f1:c4:4e  txqueuelen 1000  (Ethernet)
        RX packets 51462  bytes 69424624 (69.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7388  bytes 1113036 (1.1 MB)
        TX errors 0  dropped 2 overruns 0  carrier 0  collisions 0


```, and 

```
lspci
``` returns:

```
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation 6th-9th Gen Core Processor PCIe Controller (x16) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.2 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #2
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #17 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 06b6 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Comet Lake LPC Controller
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2019/PC SN750 NVMe SSD
3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)


```

Any ideas what might be causing this?

---

### Post by TheFu on 2020-12-16
What are the exact devices?  The onboard and dock are using different devices.

```
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
```
should provide the answer.  Run it with and without the dock connected.

**lshw -C network** can work too.  Need more than "intel" as the model.

---

### Post by mysteriousmonkey29 on 2020-12-16
With the dock connected,

```

sudo lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'

``` returns:

```

00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 160MHz
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ad51c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [80] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Latency Tolerance Reporting
    Capabilities: [164] Vendor Specific Information: ID=0010 Rev=0 Len=014 <?>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)
    Subsystem: Intel Corporation Device 0000
    Flags: fast devsel, IRQ 255
    Memory at ad200000 (32-bit, non-prefetchable) [size=1M]
    Memory at ad300000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [70] MSI-X: Enable- Count=5 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 2c-f0-5d-ff-ff-67-4a-bd
    Capabilities: [1c0] Latency Tolerance Reporting
    Capabilities: [1f0] Precision Time Measurement
    Capabilities: [1e0] L1 PM Substates

```

with it disconnected, it returns:

```

00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 160MHz
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ad51c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [80] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Latency Tolerance Reporting
    Capabilities: [164] Vendor Specific Information: ID=0010 Rev=0 Len=014 <?>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)
    Subsystem: Intel Corporation Device 0000
    Flags: fast devsel, IRQ 255
    Memory at ad200000 (32-bit, non-prefetchable) [size=1M]
    Memory at ad300000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [70] MSI-X: Enable- Count=5 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 2c-f0-5d-ff-ff-67-4a-bd
    Capabilities: [1c0] Latency Tolerance Reporting
    Capabilities: [1f0] Precision Time Measurement
    Capabilities: [1e0] L1 PM Substates


```

These look the same to me, so I tried the other command you suggested. With the dock connected,

```

sudo lshw -C network

``` returns:

```

  *-network DISABLED        
       description: Wireless interface
       product: Comet Lake PCH CNVi WiFi
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 00
       serial: 9c:29:76:f1:c4:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-58-generic firmware=50.3e391d3e.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ad51c000-ad51ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:ad200000-ad2fffff memory:ad300000-ad303fff
  *-network:0
       description: Ethernet interface
       physical id: 2
       bus info: usb@6:1.2
       logical name: enx54bf643fb650
       serial: 54:bf:64:3f:b6:50
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.11 duplex=full ip=192.168.1.132 link=yes multicast=yes port=MII speed=1Gbit/s
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: docker0
       serial: 02:42:a7:d5:a9:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes


```

With the dock disconnected, it returns:

```

  *-network DISABLED        
       description: Wireless interface
       product: Comet Lake PCH CNVi WiFi
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 00
       serial: 9c:29:76:f1:c4:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-58-generic firmware=50.3e391d3e.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ad51c000-ad51ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress cap_list
       configuration: latency=0
       resources: memory:ad200000-ad2fffff memory:ad300000-ad303fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: docker0
       serial: 02:42:a7:d5:a9:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes


```

---

### Post by TheFu on 2020-12-16
Found this about an _Intel 3101_ device: [https://commons.wikimedia.org/wiki/File:Future_Intel_CEO_Andy_Grove_holds_Intel_3101_ad_in_1969.jpg](https://commons.wikimedia.org/wiki/File:Future_Intel_CEO_Andy_Grove_holds_Intel_3101_ad_in_1969.jpg)
Don't think that is the ethernet you have.  Haven't any clue what the real device is.  I was expecting something like an intel v225-L or something like that for the device. Maybe the manual for the computer says the exact NIC model?

Intel has a few new ethernet devices that aren't well supported with current Ubuntu kernel releases.  I think some of them get better support in the 5.10.x kernels. In the meantime, you can try to figure out the exact device model and look for drivers from Intel directly. They usually have a package and good instructions to build the drivers for a kernel. Not everyone is successful getting drivers built and working.  If they don't have a DKMS part built-in, you'll need to rebuild the driver with each new kernel.

The dock connected version has usb and appears to use a realtek driver that is working. driver=r8152. That means you can use that connection to get the driver for the other plug.

Some other non-Ubuntu distros have newer kernels. Others in these forums found them and claim they worked.

---

### Post by grahammechanical on 2020-12-16
Is the ethernet adapter on the laptop disabled in the UEFI settings utility? When you installed Ubuntu was the dock connected? Were you getting an internet through the ethernet adapter in the dock and not through the ethernet adapter in the laptop?

When you open system settings>Network does the utility list the ethernet adapters in the laptop and in the dock? 

Regards

---

### Post by mysteriousmonkey29 on 2020-12-16
Haha I like the pic. I see what you're saying. I talked to MSI, and determined the following:

-my full laptop version # is GS Stealth 66 10SE-442
-my NCI is supposed to use the driver Killer LAN, E3100, which does not make a linux version. so this is probably the issue.

The support person told me that all Killer LAN drivers are very similar, so to see if I can find any, preferably E3100, that have been recreated in linux. About to look around

---

### Post by mysteriousmonkey29 on 2020-12-16
> **grahammechanical said:**
> Is the ethernet adapter on the laptop disabled in the UEFI settings utility? When you installed Ubuntu was the dock connected? Were you getting an internet through the ethernet adapter in the dock and not through the ethernet adapter in the laptop?

When you open system settings>Network does the utility list the ethernet adapters in the laptop and in the dock? 

Regards

When I got to the UEFI settings utility, it takes me to the MSI BIOS, I'm not sure if this is what you are referring to. I looked all around in there but can't find a setting related to enabling or disabling the ethernet adapter. When I installed ubuntu the dock was not connected, I used wifi.

When I got to settings-->network, it only lists "wired" if the dock is plugged in, and it says "cable unplugged" unless I plug the ethernet cable in to the dock.

---

### Post by TheFu on 2020-12-16
> **mysteriousmonkey29 said:**
> Haha I like the pic. I see what you're saying. I talked to MSI, and determined the following:

-my full laptop version # is GS Stealth 66 10SE-442
-my NCI is supposed to use the driver Killer LAN, E3100, which does not make a linux version. so this is probably the issue.

The support person told me that all Killer LAN drivers are very similar, so to see if I can find any, preferably E3100, that have been recreated in linux. About to look around

Always, always, always, check the major systems on every computer BEFORE buying for Linux support issues.
Always.

---

### Post by mysteriousmonkey29 on 2020-12-16
Yeah, I didn't do that. I found this answer, it suggests updating the kernel. I think I'm gonna try that:

[https://askubuntu.com/questions/1266180/ubuntu-20-04-killer-e3100-ax1650i-working-on-msi-gs75-10sgs](https://askubuntu.com/questions/1266180/ubuntu-20-04-killer-e3100-ax1650i-working-on-msi-gs75-10sgs)

---

### Post by mysteriousmonkey29 on 2020-12-16
It works! Updating the kernel to 5.9.10, as suggested in the above link, seems to have done the trick!

I followed these instructions:

[https://itsfoss.com/upgrade-linux-kernel-ubuntu/#ukuu](https://itsfoss.com/upgrade-linux-kernel-ubuntu/#ukuu)

ukuu was not detecting kernels beyond 5.7.1, so I did the manual installation method. The low-latency kernel failed to install correctly, so I then had to go to advanced boot settings to boot from 5.9.10-generic, and then removed 5.9.10-lowlatency to avoid the problem in the future.

Thanks for the help!

---

### Post by TheFu on 2020-12-16
Thanks for reporting back with confirmation that the solution you found worked!
Please help the community by marking this thread SOLVED in the Thread Tools button near the top of the page.

---

