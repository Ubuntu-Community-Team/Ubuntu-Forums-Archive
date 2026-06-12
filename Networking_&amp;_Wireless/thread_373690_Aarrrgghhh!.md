---
title: "Aarrrgghhh!"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-03-01
ok...here's the history.
 was was having problems setting up my wireless card. After much struggle, finally got it to turn on. Can't test it yet because I am not near a wireless source. 
But I was surfing around (through ethernet connection) on this forum and decided to reboot to see if the wireless card would activate automatically. WOW! It did! But guess what? i can not browse to any web site. I can ping plenty. Ping my router, gateway, then a few DNS' that I know. All good, but I can not surf the web through firefox.
The ethernet connection is activated and set as default gateway device. I deactivated the wireless card, still no go. 
What to do?
Thanx in advance

---

### Post by dbott67 on 2007-03-01
Can you please post the output of the following 3 commands:

```
dbott@dapper:~$ **cat /etc/network/interfaces **
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

```
dbott@dapper:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

```
dbott@dapper:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

-Dave

---

### Post by dbott67 on 2007-03-01
Also, can you please describe your network/ISP setup and any other devices (cable modem, NAT firewall, router, etc.).

Thanks.

---

### Post by lsutiger on 2007-03-01
I am not believeing this. I went ahead and setup a static ip just for giggles....well it worked! The I switched back to DHCP, and now it is working again! I do not know what to say!
Thanx for the quick response though!

---

### Post by lsutiger on 2007-03-07
OK - I did a reinstall to dual boot, now my wireless card is not showing in network settings. It was there before I ran some comands with ndiswrapper.
Here is the response to the code:
```
complexity@complexity-laptop:~$  cat /etc/network/interfaces
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
eth1 is wireless

```
complexity@complexity-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:C0:23:F8
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fec0:23f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1331979 (1.2 MiB)  TX bytes:228354 (223.0 KiB)
          Interrupt:169 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

does not show up there

```
complexity@complexity-laptop:~$  route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

