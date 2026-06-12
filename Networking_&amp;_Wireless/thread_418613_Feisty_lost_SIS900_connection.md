---
title: "Feisty lost SIS900 connection"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by atollic on 2007-04-22
In Kubuntu 6.10 my onboard SIS900 network interface didn't setup correctly. Ifconfig showed HWaddr: FF:FF:FF:FF:FF:FF.
I managed to fix this by adding line

   hwaddress ether 00:0b:6a:3a:30:a6

in my /etc/network/interfaces.

Now i've installed Feisty, but this method doesn't work anymore. Manually adding hwaddress won't help.

I've tried:  ifconfig eth1 hw ether 00:0b:6a:3a:30:a6 up
many times while disabling and enabling nic from system settings. This worked once, but can't do it anymore.

Any ideas about this?

Here are few outputs:


ifconfig:

```
eth1      Link encap:Ethernet  HWaddr FF:FF:FF:FF:FF:FF
          inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10202 (9.9 KiB)  TX bytes:398 (398.0 b)
          Interrupt:19 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

extracts from dmesg:

```
[   96.703078] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   96.712301] 0000:00:04.0: Using transceiver found at address 1 as default
[   96.712984] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 19, ff:ff:ff:ff:ff:ff.

[  106.281565] eth1: Media Link On 100mbps full-duplex

[  198.986073] NET: Registered protocol family 10
[  198.986194] lo: Disabled Privacy Extensions
[  209.703768] eth1: no IPv6 routers present

```

/etc/network/interfaces:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
        hwaddress ether 00:0b:6a:3a:30:a6

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```
lspci:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```


lshw -C network:

```
  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth1
       version: 91
       serial: ff:ff:ff:ff:ff:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:cfffc000-cfffcfff irq:19
```

---

### Post by atollic on 2007-04-23
Now I've managed to get my internet connection working by doing this manually after every boot:

1) sudo ifconfig eth1 down
2) sudo ifconfig eth1 hw ether 00:0b:6a:3a:30:a6 up
3) sudo dhclient3

I believe that automatic dchp fails at startup because Feisty fails to assign correct hardware address to my network card. 
But can anyone tell me why this happens although I have added the correct hwaddress in to my /etc/network/interfaces?

---

