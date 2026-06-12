---
title: "[SOLVED] Wireless not detected/working after installing Intrepid"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by mb_webguy on 2008-11-03
With Hardy, I had to use ndiswrapper to get wireless working, but otherwise it was a fairly simple procedure.  After installing Intrepid this morning, however, I can't get Ubuntu to even recognize my wireless card.  I've tried enabling the wl driver in the Restricted Drivers Manager, and I've tried using ndiswrapper with the Windows driver, but neither works.  

My wireless card is a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03).  When I install the Windows driver using the ndisgtk GUI, it says that the hardware is present.  If I run Hardware Testing from the Administration menu, the card is likewise detected.  Otherwise, it's as if the card doesn't exist.  

Here's the output of "iwconfig":```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

... and "ifconfig":```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:99:32:6b  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe99:326b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2017540 (2.0 MB)  TX bytes:510748 (510.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15688 (15.6 KB)  TX bytes:15688 (15.6 KB)
```

... and "sudo lshw -C network":```
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
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:99:32:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:36:b3:35:89:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I *really* need to get wireless working again, but I'm stymied. Help!

EDIT:  Following the suggestions on [this thread]("http://ubuntuforums.org/showthread.php?t=968028") seemed to help.  I can see and use my wireless card now, but it doesn't seem very reliable.  I'll mark this solved, but I hope someone comes up with a better solution.

---

