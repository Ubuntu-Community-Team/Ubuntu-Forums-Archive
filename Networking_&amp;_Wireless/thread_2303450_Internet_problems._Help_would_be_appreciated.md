---
title: "Internet problems. Help would be appreciated"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by mceak70 on 2015-11-18
I am relatively new to Ubuntu, and I am getting some issues with my ethernet connection. I am running 15.04, but I had a similar issue and 14.04.3. What is going on is at first, it would not recognize my ethernet connection at all. After browsing forums for a bit, I found some solutions, but they only got me partway there. As of right now, I am running 15.04 on my newly built computer. When I boot up, it says that I connected to my router pretty fast. I tried pinging it after firefox wouldn't load up, and it says network not found. I don't have a wireless card to try and add anything, so that isn't an option. If anybody could help me that would be great.

---

### Post by Bucky Ball on 2015-11-18
*Thread moved to **Networking & Wireless**.*

Welcome. Perhaps start by opening a terminal and copying this in:

```
sudo lshw -C network
```

Post the output here between code tags, please (last link in my signature). 

Sounds crazy, but have you tried another cable?

---

### Post by mceak70 on 2015-11-19
Here is the output, sorry for waiting to reply for so long.
```
  *-network              
       description:Ethernet interface
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: RealtekSemiconductor Co., Ltd.
       physical id: 0
       bus info:pci@0000:03:00.0
       logical name:enp3s0
       version: 0c
       serial:fc:aa:14:c8:aa:9e
       size: 1Gbit/s
       capacity:1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration:autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPIduplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yesport=MII speed=1Gbit/s

       resources:irq:29 ioport:d000(size=256) memory:fe100000-fe100fff memory:da100000-da103fff
```
Also I do not have another cord to try, but I can get one if there aren't any other options

---

### Post by mceak70 on 2015-11-21
I did more research to try and find more information and here is what I found. When I entered in the command *route*, the table was empty. Also I tried various other ways of connecting to the network, one of which involved using the modem directly, not through the router. None of that worked. If someone could help me I would be ever grateful. On a side note, is there a way to install wine using usb?

---

### Post by The Cog on 2015-11-21
That's the same interface card I have, and I have never had any problems with it - so it's not a general problem with your hardware.


```
steve@StevePC:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 06
       serial: bc:5f:f4:2a:cf:24
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:28 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff
```
```
This is the driver I seem to be using - r8169:
steve@StevePC:~$ lspci -v
< snip lots of other stuff>
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
	Subsystem: ASRock Incorporation Motherboard (one of many)
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at e800 [size=256]
	Memory at f8fff000 (64-bit, prefetchable) [size=4K]
	Memory at f8ff8000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
```

You could check that you have the same driver running.
Also, can you post the output of these commands:
```
ip link
ifconfig
sudo dhclient -v
```

---

### Post by mceak70 on 2015-11-21
Everything looks the same except for version and IRQ number. My version is 0c and IRQ is 27 I think. The driver is the same. Here are the requested outputs.
```
~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueuestate UNKNOWN mode DEFAULT group default
    link/loopback00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000

    link/etherfc:aa:14:c8:aa:9e brd ff:ff:ff:ff:ff:ff
```
```
~$ ifconfig
enp3s0    Linkencap:Ethernet  HWaddrfc:aa:14:c8:aa:9e  
          inet6 addr:fe80::feaa:14ff:fec8:aa9e/64 Scope:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3errors:0 dropped:141 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RXbytes:41058 (41.0 KB)  TX bytes:494(494.0 B)
 
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:65536  Metric:1
          RXpackets:930 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:0

          RXbytes:72547 (72.5 KB)  TX bytes:72547(72.5 KB)
```
```
~$ sudo dhclient -v
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
 
Listening on LPF/enp3s0/fc:aa:14:c8:aa:9e
Sending on  LPF/enp3s0/fc:aa:14:c8:aa:9e
Sending on  Socket/fallback
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 3(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 3(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 8(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 19(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 16(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 14(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 7(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 13(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 15(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 7(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 15(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 10(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 8(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 14(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 18(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 19(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 11(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 18(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 16(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 21(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 8(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 13(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 12(xid=0x9e700d25)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 13(xid=0x9e700d25)
No DHCPOFFERS received.

No working leases in persistent database - sleeping.
```

---

### Post by The Cog on 2015-11-21
OK, here'e what I get from the output:
It can see the cable is connected and working (LOWER_UP in the ip link output, also RUNNING in ipconfig).

But it seems to have problems transmitting packets. "TX packets:3 errors:0 dropped:141 overruns:0 carrier:0" Succesfully transmited 3 packets, dropped 141 for some unknown reason. Here is mine for comparison:
```
enp3s0    Link encap:Ethernet  HWaddr bc:5f:f4:2a:cf:24  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe2a:cf24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35286870 (35.2 MB)  TX bytes:2732199 (2.7 MB)
```

If you were to look at ifconfig before and after trying dhclient, my guess is that you would see that every outgoing config request had actually been dropped. I can't imagine why it is happening, but I think this is a low-level hardware issue. Maybe a new cable would fix it. I wish I could help more, but all I can say is I think the fact that it is dropping output packets is the reason you can't get allocated an IP address - the packets are not actually leaving the machine.

---

### Post by Bucky Ball on 2015-11-21
Installing Wine via USB is the stuff of another thread. Please post one for it if you need help with that. Good luck. :)

---

