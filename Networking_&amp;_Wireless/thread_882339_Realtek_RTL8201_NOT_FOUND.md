---
title: "Realtek RTL8201 NOT FOUND"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by ruckstande on 2008-08-06
I just installed Ubuntu 8.04 on my computer. I have a new Biostar NF4 4X-A7 mobo with a Realtek RTL8201 built in ethernet adapter. I didn't have this problem with my defunct Asus board and this is really frustrating. I can't really find anything about this adapter not being found. Please help.

---

### Post by ruckstande on 2008-08-06
Okay this is really disheartening. Am I correct in assuming the NVIDIA nForce4 4x chipset isn't compatible with Ubuntu?

---

### Post by ruckstande on 2008-08-08
Anyone know anything about this? I was really hoping to be able to start this project soon but I've hit a big roadblock.

---

### Post by jon armand on 2008-08-08
I have a Jensen pcmcia wireless adapter, which has a realtek chip inside (RTL8180L). It works fine under 6.06 and 6.10 and Vector, but not under 7.04 and up. 
lspci returns the following:
jon@jon-laptop:~$ sudo lspci
Password:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)




How do I make this pcmcia wifi card work under 7.04?

Any suggestion is appreciated!:confused::)






b.t.w. my pc is an old dell laptop (latitude cpx 500 with 384 MB ram)

---

### Post by chili555 on 2008-08-08
"Not Found" is a bit vague, but let me feel around in the dark and see what I can do. I think this is supposed to use the module *forcedeth.* Please open a terminal and do:```
sudo modprobe forcedeth
sudo lshw -C network
```Did your Realtek get a logical name, ideally eth0? If so, please do:```
sudo dhclient eth0 
```Did you get an IP address?

If none of this works, please let us see:```
dmesg | grep -i eth
```Thanks.

---

### Post by loboc on 2008-08-08
Go into the BIOS and turn PnP aware OS to "off"

---

### Post by ruckstande on 2008-08-08
> **loboc said:**
> Go into the BIOS and turn PnP aware OS to "off"
I'll try that first thing. No nothing says eth0. Nothing appears at all. When I say "No device Found" when I click on the networking icon next to the speaker it says "No Device Found".

---

### Post by ruckstande on 2008-08-10
> **chili555 said:**
> "Not Found" is a bit vague, but let me feel around in the dark and see what I can do. I think this is supposed to use the module *forcedeth.* Please open a terminal and do:```
sudo modprobe forcedeth
sudo lshw -C network
```Did your Realtek get a logical name, ideally eth0? If so, please do:```
sudo dhclient eth0 
```Did you get an IP address?

If none of this works, please let us see:```
dmesg | grep -i eth
```Thanks.


Okay, I installed a netgear card just to get this box online. That is identified as eth0. The other device is eth1. Here is the result of sudo lshw -C network:

>   *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 00
       serial: 00:40:f4:57:b5:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full latency=32 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s


Here is the result of sudo dhclient eht1

> There is already a pid file /var/run/dhclient.pid with pid 6517
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:e0:4c:eb:af:59
Sending on   LPF/eth1/00:e0:4c:eb:af:59
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Now here is dmesg | grep -i eth

> [   25.445625] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   25.965188] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:e0:4c:eb:af:59
[   25.965194] forcedeth 0000:00:0a.0: highdma csum timirq lnktim desc-v3
[   25.967497] natsemi eth1: NatSemi DP8381[56] at 0xfe9ff000 (0000:01:08.0), 00:40:f4:57:b5:bc, IRQ 19, port TP.
[   27.905169] Driver 'sd' needs updating - please use bus_type methods
[   27.905326]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   41.027679] udev: renamed network interface eth0 to eth1
[   41.059532] udev: renamed network interface eth1_rename to eth0
[   41.064290] eth0: DSPCFG accepted after 0 usec.
[   41.064298] eth0: link up.
[   41.064311] eth0: Setting full-duplex based on negotiated link capability.
[  119.925526] eth0: no IPv6 routers present
[  656.769606] eth1: link down.
[  714.696401] eth1: link up.
[  714.698041] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  716.188745] eth0: Autonegotiation advertising 0x5e1  partner 0x00.
[  716.188756] eth0: link down.
[  302.704198] eth1: no IPv6 routers present
[  402.507104] eth1: no IPv6 routers present
[ 1061.799006] eth0: Autonegotiation advertising 0x5e1  partner 0x45e1.
[ 1061.799017] eth0: link up.


---

### Post by ruckstande on 2008-08-10
One other thing, Ubuntu now sees the card but not as a Realtek as described in the motherboard manual but as an Nvidia Corp CK804 Ethernet adapter.

---

### Post by ruckstande on 2008-08-10
I ran this command as well: ifconfig -a

> eth0      Link encap:Ethernet  HWaddr 00:40:f4:57:b5:bc  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe57:b5bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:252349613 (240.6 MB)  TX bytes:7836196 (7.4 MB)
          Interrupt:19 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:eb:af:59  
          inet6 addr: fe80::2e0:4cff:feeb:af59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:804 (804.0 B)  TX bytes:6211 (6.0 KB)
          Interrupt:18 

eth1:avahi Link encap:Ethernet  HWaddr 00:e0:4c:eb:af:59  
          inet addr:169.254.8.179  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97728 (95.4 KB)  TX bytes:97728 (95.4 KB)



---

