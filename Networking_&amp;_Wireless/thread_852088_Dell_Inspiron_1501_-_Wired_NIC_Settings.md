---
title: "Dell Inspiron 1501 - Wired NIC Settings"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Gomezie on 2008-07-07
Hey folks!

Recently switched to Ubuntu (Hardy) so bare with me :)

I have successfully connected to the internet with both my WIFI and wired card on this laptop.. but I seem to be having a wierd issue:

When at work I use the wired connection, and set a static IP.

Upon a reboot.. this IP setting still remains, but when I try to access the internet I get no response, until I change my static IP to something else.

Once I have changed my client IP .. everything instantly works.. really got me confused here.

Any ideas or tips you could give me would be great!

Cheers

Gomezie

**_ifconfig_**
```

eth0      Link encap:Ethernet  HWaddr 00:19:b9:68:80:71  
          inet addr:213.249.168.196  Bcast:213.249.168.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe68:8071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:213850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:853 txqueuelen:1000 
          RX bytes:143469361 (136.8 MB)  TX bytes:2439449 (2.3 MB)
          Interrupt:21

```

**_sudo lshw -C network_**
```

  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:7f:c6:89
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:68:80:71
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=213.249.168.196 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=10MB/s

```

---

### Post by Gomezie on 2008-07-07
No one anything to add? :(

Even if it could be something on startup that I could check

---

