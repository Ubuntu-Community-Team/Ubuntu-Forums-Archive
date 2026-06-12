---
title: "How to choose network interface?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by uyguy on 2007-10-25
Hi,

I recently followed this quide [http://ubuntuforums.org/showthread.php?t=166617]("http://ubuntuforums.org/showthread.php?t=166617") to get my laptop connected throw my GPRS cell phone via USB.

If I type in a terminal ifconfig before trying to connect with the cell phone I get:
```

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:4B:AA:D3  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:02:C7:70:E5  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fec7:70e5/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1492  Metric:1
          RX packets:560 errors:0 dropped:585 overruns:0 frame:0
          TX packets:343 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:16897130 (16.1 MB)  TX bytes:1349103 (1.2 MB)
          Interrupt:18 Base address:0x4000 Memory:da000000-da000fff 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:2374 (2.3 KB)  TX bytes:2374 (2.3 KB)

```

Then I plug my cell phone via USB, and type sudo wvdial and I get:
```

adri@adri-laptop:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Thu Oct 25 14:56:30 2007
WvDial<Notice>: Pid of pppd: 6353
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: local  IP address 10.12.27.153
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: primary   DNS address 200.40.30.245
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]
WvDial<*1>: secondary DNS address 200.40.220.245
WvDial<*1>: pppd: H&#65533;[06][08]H&#65533;[06][08]

```

I think it means it is connected using ppp0 interface, and besides in my cell apears like it is connected.

Then I type ifconfig again:
```

adri@adri-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:4B:AA:D3  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:02:C7:70:E5  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fec7:70e5/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1492  Metric:1
          RX packets:235 errors:0 dropped:617 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:17721298 (16.9 MB)  TX bytes:1421421 (1.3 MB)
          Interrupt:18 Base address:0x4000 Memory:da000000-da000fff 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:2374 (2.3 KB)  TX bytes:2374 (2.3 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet addr:10.12.27.153  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT CORRIENDO NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:64 (64.0 b)  TX bytes:153 (153.0 b)

```

Now is present the new network interface (ppp0), but I don't know how to access the internet throw it. It uses eth1, wich is my wifi card.

Please I need help. Thanks.

---

### Post by spd106 on 2007-10-25
Try checking the routing table with the following terminal command.

```
ip route show
```

You should have the first line that starts with default pointing at the ppp0 device, no the eth1 device. You can change this manually by entering a couple of commands, but it's likely to get changed back by network manager if your wireless card is in roaming mode. The best solution would be to either temporarily disable the eth1 interface or switch it to a static configuration.

---

