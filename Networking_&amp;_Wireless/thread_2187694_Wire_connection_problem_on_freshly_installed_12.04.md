---
title: "Wire connection problem on freshly installed 12.04"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by sylvain.lannebere on 2013-11-13
Hi,

I have a new computer where I installed ubuntu 12.04 and I have no wire connection (ubuntu says the wire is unplugged and my ethernet card is producing no light). I try to change the version to 13.10 but I have the same problem.

Here are the response of the different commands:
```
cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



``````
sudo lshw -C network 
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 88:51:fb:53:c3:dc
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:d000(size=256) memory:f7c04000-f7c04fff memory:f7c00000-f7c03fff



``````
ifconfig 
eth0      Link encap:Ethernet  HWaddr 88:51:fb:53:c3:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2528 (2.5 KB)  TX bytes:2528 (2.5 KB)



``````
lspci -nn | grep -i net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)

```
Does anyone has any idea of the problem? Thanks

---

### Post by grahammechanical on 2013-11-13
If networking was disabled in Ubuntu then ifconfig would only show a printout for lo. I just tried it on my machine. The printout for eth0 shows UP BROADCAST MULTICAST. That tells me that the ethernet adapter is working. But you should see UP BROADCAST RUNNING MULTICAST.

This tells me that Ubuntu has installed a driver module for that ethernet adapter card.

> broadcast=yes driver= r8169 driverversion=2.3LK-NAPI

Perhaps Ubuntu is right when it says "unplugged." Is the router/hub switched on? The ethernet adapter is not communicating with the router.

> RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

RX = Receiving. TX  = Transmitting. Data is not moving betwen Ubuntu and the router. This is what I have when I run ifconfig.

> eth0      Link encap:Ethernet  HWaddr 00:1a:92:82:db:59  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe82:db59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10283897 (10.2 MB)  TX bytes:2210187 (2.2 MB)
          Interrupt:17 

Do you see that eth0 is RUNNING and that I have many bytes being Received (RX) and Transmitted (TX). 

Regards.

---

