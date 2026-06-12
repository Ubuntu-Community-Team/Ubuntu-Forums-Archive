---
title: "wifi problems"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by JParkus on 2009-07-18
I have a compaq cq60 wifi was working. It stoped after trying to to connect to a wifi hotspot. I thought maybe it was a driver issue so I tried the non-free madwifi driver nothing. This is what I have got so far

lspci shows 
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci, ath5k
lshw shows 
 *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:50:0b:a8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:3c:b9:24:4f:6b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by JParkus on 2009-07-18
parkus@parkus-laptop:~$ lspci -nn | grep 'Atheros'
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
parkus@parkus-laptop:~$  ifconfig wlan0
wlan0: error fetching interface information: Device not found
parkus@parkus-laptop:~$ lsmod | grep "ath5k"
parkus@parkus-laptop:~$ lsmod | grep "ath5k"
parkus@parkus-laptop:~$ dmesg | grep "ath5k"
parkus@parkus-laptop:~$ 
parkus@parkus-laptop:~$ dmesg | grep "ath5k"
parkus@parkus-laptop:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

parkus@parkus-laptop:~$ # /etc/init.d/networking restart
parkus@parkus-laptop:~$ 


Still not much luck but more info

---

### Post by JParkus on 2009-07-18
GOT IT 

here is where i found it
[http://ubuntuforums.org/showthread.php?t=798485&page=3](http://ubuntuforums.org/showthread.php?t=798485&page=3)

---

