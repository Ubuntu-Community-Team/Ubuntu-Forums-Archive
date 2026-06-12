---
title: "Wireless Driver Problems?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by kayaksmak on 2009-10-08
so, i've got some wireless driver problems and I have no clue what to do with them.  I think the driver isn't even installed.  

here's the network hardware lister 
```
   Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.13)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

ryan@Wilder:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:70:fd:ee
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=half firmware=5755m-v3.29 ip=199.111.230.228 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:6d:87:ed:cc:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

---

### Post by cariboo on 2009-10-08
> **kayaksmak said:**
> so, i've got some wireless driver problems and I have no clue what to do with them.  I think the driver isn't even installed.  

here's the network hardware lister 
```
   Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.13)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

ryan@Wilder:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=b43-pci-bridge** latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:70:fd:ee
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=half firmware=5755m-v3.29 ip=199.111.230.228 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:6d:87:ed:cc:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

I've highlighted the driver in the above quote, it is loaded, so your problem is elsewhere.

Could you paste the output of:

```
sudo iwconfig
```

and 

```
ifconfig
```

---

### Post by kayaksmak on 2009-10-08
here they are

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```[CODE] 
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:21:70:70:fd:ee  
          inet addr:199.111.230.228  Bcast:199.111.231.255  Mask:255.255.252.0
          inet6 addr: fe80::221:70ff:fe70:fdee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129599 errors:36783 dropped:33 overruns:0 frame:85
          TX packets:70016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:36715 txqueuelen:1000 
          RX bytes:154428783 (154.4 MB)  TX bytes:7297953 (7.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
[\CODE]

---

