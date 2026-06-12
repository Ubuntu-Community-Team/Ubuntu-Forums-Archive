---
title: "Check NIC"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-17
I lost Internet connection and my provider claims that I need to change my network card. I can "see" it doing:

```
lspci |grep eth
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
```

but I've also:

```
dmesg |grep eth
[   19.737197] eth0: VIA Rhine II at 0x1b400, 00:0b:6a:f2:1d:fc, IRQ 17.
[   19.737911] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.

[   29.645427] eth0: link down

[   48.175872] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  455.575087] eth0: link down
[  455.575257] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

The problem comes from not getting any valid IP adress from DHCP

```
ifconfig
eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr  
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2280 (2.2 KiB)  TX bytes:2280 (2.2 KiB)
```

I have tried many things:

```
felix@ordinador:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

```
felix@ordinador:~$ sudo mii-diag
Password:
Using the default interface 'eth0'.
Basic registers of MII PHY #1:  3000 7849 0000 8201 01e1 0000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x7849 ... 7849.
   Link status: not established.
   End of basic transceiver information.

felix@ordinador:~$ sudo mii-tool
eth0: no link
```

```
felix@ordinador:~$ sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5148
killed old client process, removed PID file
Listening on LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.127.36.140 port 67

felix@ordinador:~$ sudo mv /var/run/dhclient.eth0.pid /var/run/dhclienteth0pidbackup

felix@ordinador:~$ sudo ifconfig eth0 up

felix@ordinador:~$ sudo dhclient eth0
Listening on LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
felix@ordinador:~$ nautilus /etc/network/
```

But I still have no connection. Do you believe that I need to change my NIC ?

---

