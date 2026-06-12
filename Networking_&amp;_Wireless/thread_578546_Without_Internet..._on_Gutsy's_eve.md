---
title: "Without Internet... on Gutsy's eve"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-17
I lost Internet connection. Given all this output, can anyone determine if my problem is:

- Damaged DSL-MODEM

- Damaged, malfunctioning or disconfigured NIC. I think not, but not sure

- System problem (i.e.: I need to reinstall Ubuntu)

- Other ? 

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

I recieve no valid IP adress from DHCP

```
sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: no


sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:0b:6a:f2:1d:fc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:b400-b4ff iomemory:e5000000-e50000ff irq:17
```

Does[FONT="Courier New"] Link detected: no[/FONT] mean that the PC can't reach the modem? The PC-LINK light is off, but the wire-cable is well attached!

```
sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5148
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.127.36.140 port 67


felix@ordinador:~$ sudo mv /var/run/dhclient.eth0.pid /var/run/dhclienteth0pidbackup


felix@ordinador:~$ sudo ifconfig eth0 up


felix@ordinador:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                         RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5340
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.127.36.140 port 67
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   LPF/eth0/00:0b:6a:f2:1d:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                                                        [ OK ]
```

```
route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

```
sudo mii-diag
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

I'm sorry I've started a few threads, but I just don't know what to do

---

### Post by Druke on 2007-10-17
whats your setup? computer->modem or comp->router->modem

---

### Post by slink on 2007-10-17
> whats your setup? computer->modem or comp->router->modem

computer->modem

---

### Post by slink on 2007-10-17
[FONT="Courier New"]dmesg |grep eth[/FONT]

Does it help?

```
[   19.737197] eth0: VIA Rhine II at 0x1b400, 00:0b:6a:f2:1d:fc, IRQ 17.
[   19.737911] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.

[   29.645427] eth0: link down

[   48.175872] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  455.575087] eth0: link down
[  455.575257] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by Druke on 2007-10-17
Did it work before gutsy? It could be your NIC. I had the exact same problem with a server I was running, the NIC didn't have enough strength to be recognized by my modem's DHCP and thus the link light was off. luckily I had two nics on that pc (one for dhcp to the rest of the house, on for internet incoming) I simply reversed them and all was well.

---

### Post by slink on 2007-10-17
> Did it work before gutsy?

I'ts been working half a year, since 7.04

> It could be your NIC

What makes you think that?


The story of it is that I lost Internet during a lightning storm. Now the provider claims that is my NIC's fault. I'd like to be sure about that before installing another NIC.

---

### Post by Druke on 2007-10-17
Ah! well then it could be one or both, do you have another unit to test it against? maybe a router laying around that you can connect to? My old provder tried to pull the same crap once, they could get into my router but nothing could get out the other end, finally had to take the thing up there and show them in person. (glad we dropped charter cable)

anyways you just need to figure out what really isn't working, so you jsut need to connect your ethernet to something else and see if it connects, if you can connect to a router, your nic is fine

---

### Post by slink on 2007-10-17
Thanks for the hints, Druke. Maybe I still have an old router at the bottom of a wardrobe... or I can try to connect a laptop on my stubborn modem.

---

### Post by rickyjones on 2007-10-17
> **slink said:**
> 
The story of it is that I lost Internet during a lightning storm. Now the provider claims that is my NIC's fault. I'd like to be sure about that before installing another NIC.

Lightning storm and the first thing your provider says is that the computer NIC is at fault? I'd point more to the modem right now personally. What kind of modem is it? What lights are on? Who is the service provider? (I did a lot of work with SBC/ATT DSL here in the states...)

Easiest thing to do personally would be to buy a new modem from a computer store to test with. If it works with the new modem then you have internet back and you're out 70 bucks (depending on what you buy). If it doesn't work then you can return the modem and you're out 0 bucks. Then try buying a new NIC.... :)

-Richard

---

