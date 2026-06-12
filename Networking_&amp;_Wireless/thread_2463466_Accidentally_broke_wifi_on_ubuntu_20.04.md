---
title: "Accidentally broke wifi on ubuntu 20.04?"
date: 2021-06-11
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2021-06-11
Hello, I am running ubuntu 20.04 on an MSI GS66 Stealth, running kernel 5.9.10-050910-generic #202011221708 SMP Sun Nov 22 18:07:21 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

I was playing around with libpcsc and somehow accidentally deleted the network manager.. Fortunately, I was able to get it back by connecting to ethernet with ```
sudo dhclient eth0
```, and then ```
sudo apt install network-manager
```

This brought back my wifi to some degree--it now detects networks and is able to connect to my wifi network. However, I am not able to access any websites. The internet is working normally on ethernet, it's just the wifi that isn't working.

Any ideas how to get it back?
```
ifconfig -a
```
produces:
```
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:13:1d:1e:7e  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp60s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.5  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::3380:2c94:c02:ca13  prefixlen 64  scopeid 0x20<link>
        ether 2c:f0:5d:67:4a:bd  txqueuelen 1000  (Ethernet)
        RX packets 91645  bytes 109767066 (109.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2050  bytes 110198 (110.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xad200000-ad2fffff  

enx54bf643fb650: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:bf:64:3f:b6:50  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3871  bytes 407097 (407.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3871  bytes 407097 (407.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.14  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::181b:ea4d:51fe:358f  prefixlen 64  scopeid 0x20<link>
        ether 9c:29:76:f1:c4:4e  txqueuelen 1000  (Ethernet)
        RX packets 4312  bytes 338727 (338.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 19850  bytes 2807412 (2.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

```
lspci
```
produces:
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

```
**sudo lshw -C network**
```
produces:
```
  *-network                 
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
       configuration: broadcast=yes driver=iwlwifi driverversion=5.9.10-050910-generic firmware=50.3e391d3e.0 QuZ-a0-hr-b0-50.u ip=10.0.0.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ad51c000-ad51ffff
  *-network
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3c:00.0
       logical name: enp60s0
       version: 02
       serial: 2c:f0:5d:67:4a:bd
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=5.9.10-050910-generic duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 memory:ad200000-ad2fffff memory:ad300000-ad303fff
  *-network:0
       description: Ethernet interface
       physical id: 2
       logical name: docker0
       serial: 02:42:13:1d:1e:7e
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       bus info: usb@6:1.2
       logical name: enx54bf643fb650
       serial: 54:bf:64:3f:b6:50
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.11.11 duplex=half firmware=rtl8153a-3 v2 02/07/20 link=no multicast=yes port=MII speed=10Mbit/s
```

Notably, my wifi settings is set to Automatic (DHCP) under IPv4, while the ethernet is set to a manual static IP of 192.168.1.5 (something that I had left over from a previous project). I've tried changing back to Automatic (DHCP) for ethernet, but the change doesn't take for some reason.

---

### Post by mysteriousmonkey29 on 2021-06-11
Update: I got the ethernet to change to Automatic (DHCP). Turns out I had to unplug the ethernet cable and plug it back in after making that change. Unfortunately, this broke my ethernet as well. Now I am accessing the internet via ethernet via a docking station plugged in via USB. This has Automatic (DCHP) selected under IPV4 as well, but it works for some reason.

Additionally, I am now unable to change the network settings from the GUI for both ethernet interfaces and the wifi. All the buttons are greyed out since that last change.

Sorry, it appears that I just made the problem worse :(

---

### Post by mysteriousmonkey29 on 2021-06-11
More weirdness: I tried switching to the 5G version of my network, and now I'm able to access the internet via wifi. But it still doesn't work with my regular network, so I'm not sure it will work for all networks.

Further, my ethernet through the built-in ethernet port is still broken, as per my last comment. It works through the USB hub though.

Really have no idea what's going on here.

---

### Post by mysteriousmonkey29 on 2021-06-11
Ok, sorry for the constantly evolving problem, but the wifi appears to be fixed now. I'm not actually sure how I fixed it, but through some combination of connecting to different networks, and restarting things, it's working again. The ethernet through the USB docking station is also working.

The last thing that isn't working is my built-in ethernet port (which I do need sometimes; I can't always be docked). It is currently stuck on a manual, static IP address under the "Network" settings-->IPv4. I have tried repeatedly to switch it back to Automatic (DHCP), but the change doesn't stick, even after turning on and off the ethernet switch in settings, restarting the network manager, unplugging/replugging in the cable, and restarting. I think that switching to an automatic IP will probably fix the internet, but I can't get the changes to stay for some reason.

```
ifconfig
``` currently returns:

```
 docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:29:36:02:f8  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp60s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.5  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::3380:2c94:c02:ca13  prefixlen 64  scopeid 0x20<link>
        ether 2c:f0:5d:67:4a:bd  txqueuelen 1000  (Ethernet)
        RX packets 7519  bytes 9197227 (9.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 315  bytes 17852 (17.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xad200000-ad2fffff  

enx54bf643fb650: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:bf:64:3f:b6:50  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1825  bytes 167564 (167.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1825  bytes 167564 (167.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.14  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::181b:ea4d:51fe:358f  prefixlen 64  scopeid 0x20<link>
        ether 9c:29:76:f1:c4:4e  txqueuelen 1000  (Ethernet)
        RX packets 13245  bytes 15259709 (15.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6328  bytes 1832278 (1.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### Post by mysteriousmonkey29 on 2021-06-11
Alright, I fixed that ethernet issue as well! I ended up running:

```
sudo nmtui
```

and  deleting the ethernet interface with the manual IP configuration that  was causing problems. So everything is working now, although I don't  have a good handle on what was wrong in the first place, unfortunately.

---

