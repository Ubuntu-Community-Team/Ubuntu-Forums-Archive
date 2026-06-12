---
title: "Another (wired) network connection problem"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by brain99 on 2007-02-26
After installing ubuntu 6.10 (desktop version) I have no network connectivity.

Going to a web site with firefox results in an immediate error (I don't remember the exact message), I couldn't ping, could not resolve any domain name - in short: no connectivity at all.

I noticed that my NIC had gotten an ipv6 address, so I figured that might have been the problem and disabled ipv6.

Now it won't acquire an ip address at all - dhcp doesn't seem to work. It works in Windows (dual boot) so this must be an Ubuntu problem.

Okay, now some more information - I have searched the forums a bit and so I'll include the output of some commands here:

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:17:31:D6:CA:1D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1368 (1.3 KiB)
          Interrupt:169 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:13:02:BB:C0:4B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:15 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xa000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

route -n
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
eth0 is my wired connection, eth1 is my wireless connection (I first want to get the wired one working before I start messing with the wireless one)

sudo lshw -class network
```
  *-network               
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:d6:ca:1d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=r1000 driverversion=1.05 firmware=N/A link=yes multicast=yes port=twisted pair
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:169
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:bb:c0:4b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:fe1ff000-fe1fffff irq:177
```

sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:17:31:d6:ca:1d
Sending on   LPF/eth0/00:17:31:d6:ca:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
```

I hope you guys can help me, I really want to start using Linux.

Roel

---

### Post by ukripper on 2007-02-26
> **brain99 said:**
> After installing ubuntu 6.10 (desktop version) I have no network connectivity.

Going to a web site with firefox results in an immediate error (I don't remember the exact message), I couldn't ping, could not resolve any domain name - in short: no connectivity at all.

I noticed that my NIC had gotten an ipv6 address, so I figured that might have been the problem and disabled ipv6.

Now it won't acquire an ip address at all - dhcp doesn't seem to work. It works in Windows (dual boot) so this must be an Ubuntu problem.

Okay, now some more information - I have searched the forums a bit and so I'll include the output of some commands here:

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:17:31:D6:CA:1D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1368 (1.3 KiB)
          Interrupt:169 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:13:02:BB:C0:4B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:15 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xa000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

route -n
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
eth0 is my wired connection, eth1 is my wireless connection (I first want to get the wired one working before I start messing with the wireless one)

sudo lshw -class network
```
  *-network               
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:d6:ca:1d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=r1000 driverversion=1.05 firmware=N/A link=yes multicast=yes port=twisted pair
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:169
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:bb:c0:4b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:fe1ff000-fe1fffff irq:177
```

sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:17:31:d6:ca:1d
Sending on   LPF/eth0/00:17:31:d6:ca:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
```

I hope you guys can help me, I really want to start using Linux.

Roel




Try below commands in terminal:

$ sudo ifdown eth0
$ sudo ifup eth0

check in network settings if eth0 gets enabled.

---

### Post by brain99 on 2007-02-26
> **ukripper said:**
> Try below commands in terminal:

$ sudo ifdown eth0
$ sudo ifup eth0

check in network settings if eth0 gets enabled.

I had already tried disabling and re-enabling my adapter, but tried again anyways (since my previous attempt was through the gui for configuring the network adapters).

Doing it through the shell didn't help any more than my earlier attempt with the gui... :(

Anyway, here is the output of these commands:
sudo ifdown eth0
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:17:31:d6:ca:1d
Sending on  LPF/eth0/00:17:31:d6:ca:1d
Sending on  Socket/fallback
```

sudo ifup eth0
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:17:31:d6:ca:1d
Sending on  LPF/eth0/00:17:31:d6:ca:1d
Sending on  Socket/fallback
DHCPDISCOVERY on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVERY on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVERY on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVERY on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVERY on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVERY on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

