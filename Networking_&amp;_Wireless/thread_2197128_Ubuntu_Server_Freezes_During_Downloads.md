---
title: "Ubuntu Server Freezes During Downloads"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by Xaotique on 2014-01-02
When downloading a file on Ubuntu Server 13.10, the whole system seems to freeze up.  It will unfreeze and freeze again many times during the download.  I've tried FTP to the server, using wget through SSH, and both seem to act the same, except FTP client will timeout.

I've tried over LAN and from a remote server, and it happens every time.  Usually around 30% of a 700MB file.  If this happens to be a known bug, should I think about moving to a Debian Server if it's a problem?

Note that when I say it freezes, I mean everything.  SSH doesn't return, the file stops downloading for a little, and the web server doesn't respond.

```
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy
```

---

### Post by varunendra on 2014-01-05
The fact that it is a server is probably going to be the biggest hurdle for me (personally), but can we see what chip and driver you are using? The output of -
```
lspci -nnk | grep -iA2 net
```

Some more details (assuming it is a wired connection, whose logical interface name is "eth0") -
```
uname -mr
ifconfig
route -n
dmesg | grep eth0
```

---

### Post by Xaotique on 2014-01-06
Yes, it's a wired connection through a router.

```
tom@lightron:~$ lspci -nnk | grep -iA2 net
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: Elitegroup Computer Systems Device [1019:8139]
        Kernel driver in use: 8139too
```

```
tom@lightron:~$ uname -mr
3.11.0-14-generic x86_64
```

```
tom@lightron:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

```
tom@lightron:~$ dmesg | grep eth0
[    1.109345] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x000000000001ec00, 00:1b:b9:78:13:00, IRQ 20
[    5.550953] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.377481] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```

---

### Post by varunendra on 2014-01-06
You missed the output of "ifconfig".

There seem to be some parameters available with 8139too driver that you may play with (check "modinfo 8139too"), but I don't know how to check if the parameters actually stick. The /sys/module/8139too direcotry seems to have no "parameters" directory even if I load the driver with a parameter, so not sure if they actually work.

---

### Post by Xaotique on 2014-01-07
```
tom@lightron:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:78:13:00  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fe78:1300/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113157 errors:0 dropped:10 overruns:0 frame:0
          TX packets:81020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21166667 (21.1 MB)  TX bytes:18942644 (18.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70603 (70.6 KB)  TX bytes:70603 (70.6 KB)
```

And yes, it's a static IP.
```
tom@lightron:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.145
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 207.255.0.43 207.255.0.45
```

```
tom@lightron:~$ modinfo 8139too
filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/ethernet/realtek/8139too.ko
version:        0.9.28
license:        GPL
description:    RealTek RTL-8139 Fast Ethernet driver
author:         Jeff Garzik <jgarzik@pobox.com>
srcversion:     9DC1ED205DEC5DFD8F6ADAF
alias:          pci:v*d00008139sv000013D1sd0000AB06bc*sc*i*
alias:          pci:v*d00008139sv00001186sd00001300bc*sc*i*
alias:          pci:v*d00008139sv000010ECsd00008139bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
alias:          pci:v0000021Bd00008139sv*sd*bc*sc*i*
alias:          pci:v00001743d00008139sv*sd*bc*sc*i*
alias:          pci:v0000126Cd00001211sv*sd*bc*sc*i*
alias:          pci:v0000018Ad00000106sv*sd*bc*sc*i*
alias:          pci:v000002ACd00001012sv*sd*bc*sc*i*
alias:          pci:v00001432d00009130sv*sd*bc*sc*i*
alias:          pci:v000011DBd00001234sv*sd*bc*sc*i*
alias:          pci:v000014EAd0000AB07sv*sd*bc*sc*i*
alias:          pci:v000014EAd0000AB06sv*sd*bc*sc*i*
alias:          pci:v00001259d0000A11Esv*sd*bc*sc*i*
alias:          pci:v00001259d0000A117sv*sd*bc*sc*i*
alias:          pci:v000013D1d0000AB06sv*sd*bc*sc*i*
alias:          pci:v00001186d00001340sv*sd*bc*sc*i*
alias:          pci:v00001186d00001300sv*sd*bc*sc*i*
alias:          pci:v00004033d00001360sv*sd*bc*sc*i*
alias:          pci:v00001500d00001360sv*sd*bc*sc*i*
alias:          pci:v00001113d00001211sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008138sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008139sv*sd*bc*sc*i*
depends:        mii
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           use_io:Force use of I/O access mode. 0=MMIO 1=PIO (bool)
parm:           debug:8139too bitmapped message enable number (int)
parm:           multicast_filter_limit:8139too maximum number of filtered multicast addresses (int)
parm:           media:8139too: Bits 4+9: force full duplex, bit 5: 100Mbps (array of int)
parm:           full_duplex:8139too: Force full duplex for board(s) (1) (array of int)
```

---

### Post by varunendra on 2014-01-07
There seem to be dropped packets, but in comparison to received packets they are negligible. So there is clearly no packet handling problem.

As for the driver parameters, these are the ones I was talking about -
```
parm:           use_io:Force use of I/O access mode. 0=MMIO 1=PIO (bool)
parm:           media:8139too: Bits 4+9: force full duplex, bit 5: 100Mbps (array of int)
parm:           full_duplex:8139too: Force full duplex for board(s) (1) (array of int)
```

Maybe try them one at a time and see for yourself if it can make any difference. For example -
```
sudo modprobe -rv 8139too && sudo modprobe -v 8139too full_duplex=1
```

Assuming you have full physical access to the server, can you try a different card with a different chip/driver? I don't have enough experience with wired connections to trust my 'instincts', but I have a feeling it is possibly something other than the driver. May be external, or some power management issue, internal or external.

---

