---
title: "Dual NIC help, says UNSPEC?"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by Oshaka on 2007-10-05
Hello. I need some help with my networking. I am using 2 NIC's. Basically I have 2 IPs (fake for example, connected to WAN) 10.5.3.20 10.5.3.21.

- Why does eth1 encap say "UNSPEC"? . I can ping both IPs from outside the network, and load apache on both IPs .. and most the time I can send data from INSIDE the local machine from eth1. (eX: ping -I eth1 google.com = fails (once and awhile), ping -I eth0 google.com = pass)

- Why isn't their any stats collected for eth1? None in ifconfig nor iptraf

Heres my ifconfig output:

> 
eth0 Link encap:Ethernet HWaddr 00:12:17:5A:9F:E1
inet addr:10.5.3.20 Bcast:10.5.3.* Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:100376 errors:0 dropped:0 overruns:0 frame:0
TX packets:90205 errors:12 dropped:0 overruns:0 carrier:12
collisions:0 txqueuelen:1000
RX bytes:22260313 (21.2 MiB) TX bytes:55372420 (52.8 MiB)
Interrupt:209 Base address:0xac00

eth1 Link encap:UNSPEC HWaddr 00-11-D8-00-00-30-64-D1-00-00-00-00-00-00-00-00
inet addr:10.5.3.21 Bcast:10.5.3.* Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:216 (216.0 b)


ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:12:17:5A:9F:E1  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19598035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22484196 errors:12 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000 
          RX bytes:4157075260 (3.8 GiB)  TX bytes:21303944848 (19.8 GiB)
          Interrupt:209 Base address:0xac00 

eth1      Link encap:UNSPEC  HWaddr 00-11-D8-00-00-30-64-D1-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:46764 (45.6 KiB) 


interaces file

> 
auto lo
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet static

address 66.***.***.91
netmask 255.255.255.0 
broadcast 66.***.***.255
gateway 66.***.***.1 (Same as eth1)

allow-hotplug eth1
iface eth1 inet static

address 66.***.***.93
netmask 255.255.255.0 
broadcast 66.***.***.255
gateway 66.***.***.1 


---

### Post by noob12 on 2007-10-06
Check the driver on eth1.  Can you post the output of **sudo lshw -C network** ?

You've got both interfaces on the same net and my guess is the traffic is really all going through the first interface.  There are no received packets on eth1 (see the packet counts in ifconfig output).  Can you ping the second interface if you unplug the first?

You should also know that you are going to have to take precautions against ARP issues if you run both interfaces on the same net.  There was just another thread about this recently: [http://ubuntuforums.org/showthread.php?t=566908](http://ubuntuforums.org/showthread.php?t=566908)

---

### Post by mips on 2007-10-06
> **noob12 said:**
> 
You've got both interfaces on the same net and my guess is the traffic is really all going through the first interface.  There are no received packets on eth1 (see the packet counts in ifconfig output).  Can you ping the second interface if you unplug the first?

You should also know that you are going to have to take precautions against ARP issues if you run both interfaces on the same net.  There was just another thread about this recently: [http://ubuntuforums.org/showthread.php?t=566908](http://ubuntuforums.org/showthread.php?t=566908)

Recipe for disaster having two nics in the same network on one box. It is actually against TCP/IP design guidelines. I posted some stuff on this before.

---

### Post by Oshaka on 2007-10-06
lshw -C network
> 
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth0
       version: 11
       serial: 00:12:17:5a:9f:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.13-NAPI ip=66.***.***.91 latency=32 maxlatency=128 mingnt=64 multicast=yes
       resources: ioport:ac00-acff iomemory:fdeff000-fdeff3ff irq:209
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1_temp_temp
       version: 11
       serial: 00:11:d8:ed:b4:d2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.65 duplex=half firmware=5751-v3.40a latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:fddf0000-fddfffff irq:217
  *-network
       description: IEEE1394 interface
       physical id: 1
       logical name: eth1
       serial: 00:11:d8:00:00:30
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 ip=66.***.***.93 multicast=yes


---

### Post by noob12 on 2007-10-06
This indicates your second regular ethernet card is disabled, maybe just not UP, and sitting on the interface name eth1_temp_temp (how did you get there?) and your eth1 is actually your firewire interface.  (Is this really what you intend?)

That probably explains the original encapsulation question; I suspect the eth1394 driver is not reporting the encapsulation as ethernet.  I think that driver is still experimental as well.  I don't know that you should rely on it.

You might want to take a step back and try to find a more standard approach to whatever it is you are trying to do.

---

### Post by Oshaka on 2007-10-06
I intended using 2 NICs for 2 static WAN ip's rather than using IP aliases. I need 2 static IPs for the DNS servers, than use one of those statics to server ssh/ftp/http. 

I can access both inbound and outbound .. But no statistics are created for eth1. I want eth1 to function like eth0. 

How can that be achieved? 


Thanks.

---

### Post by mips on 2007-10-06
> **noob12 said:**
> 
That probably explains the original encapsulation question; I suspect the eth1394 driver is not reporting the encapsulation as ethernet.  I think that driver is still experimental as well.  I don't know that you should rely on it.


i'm pretty sure that interface is the firewire port which you can technically network through with another firewire interface but it will never support ethernet encapsulation.

The two relevant interface here are :
>         product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek

       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation

So why does the firewire port have the eth1 ip address ?

---

### Post by Oshaka on 2007-10-06
One is an onboard device (built into mobo), the other is a regular PCI NIC.

---

