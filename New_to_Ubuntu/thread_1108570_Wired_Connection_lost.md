---
title: "Wired Connection lost"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Fernzaty on 2009-03-27
I just installed Intrepid on my Acer Aspire One, the 1Gb ram and 16Gb sd storage version. After the installation, it told me there was a load of updates to be done, so I did, using a wired connection cause I knew the wireless connection would need a little work. All fine and well (although it did take some time), and at the end, it told me I had to reboot. The problem is, after that reboot, I've now lost my wired connection. Can anyone advise? My router is working fine by the way, I'm writing and posting this via my desktop just fine.

---

### Post by mikewhatever on 2009-03-27
You should post some relevant info to start with. How about the outputs of **ifconfig** and **sudo lshw -C network**.

---

### Post by superprash2003 on 2009-03-28
your wired connection is probably not getting an ip address.. you could try typing **sudo dhclient eth0** where eth0 is the wired interface

---

### Post by Fernzaty on 2009-03-28
Okay, the outputs of the first two commands are

ipconfig

eth0      Link encap:Ethernet  HWaddr 00:23:8b:5a:95:d1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:201326580 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo lshw -C network

*-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: ff
       serial: 00:23:8b:5a:95:d1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:73:a8:c5:24:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

and the third one, sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:23:8b:5a:95:d1
Sending on   LPF/eth0/00:23:8b:5a:95:d1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

A bit of general looking around the forum boards last night, just before going to bed, and I found a thread saying something about the latest update killing wired connections and rolling those back till a fix comes along. Try as I might, I can't find that thread this morning, although even if I could, I wouldn't have a clue how to roll back.

---

