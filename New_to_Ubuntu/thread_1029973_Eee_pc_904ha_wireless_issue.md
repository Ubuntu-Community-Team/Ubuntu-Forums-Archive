---
title: "Eee pc 904ha wireless issue"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by metzy85 on 2009-01-03
I  just bought a new eee pc 904ha and it has a atheros 5007eg wirless card in it and i cant connect to any wireless networks and in hardware drivers it says the driver is activated and currently in use but when i click on the two computers in the top right corner i cant choose and wireless networks what do i need todo?

---

### Post by Michael.Godawski on 2009-01-04
hi,

can you please post the outputs of these terminal commands?

```
sudo lshw -C network
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

They will help to determine the current status of your network.

---

### Post by metzy85 on 2009-01-05
PCI (sysfs) 
  *-network              
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:81:78:19
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.100 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:9f:4b:b4:1f:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ian@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ian@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ian@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

