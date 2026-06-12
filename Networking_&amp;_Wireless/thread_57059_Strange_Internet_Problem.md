---
title: "Strange Internet Problem"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by +Flip on 2005-08-15
I'v just installed Ubuntu. And at the startup my network card doesn't word properly.

I can acces my router, but cannot connect to internet.
My router is cofigured properly, because i can acces internet with xp pro(dual boot)

If tried
```

ifconfig eth0 down
ifconfig eth0 up

``` 

Here is my ifconfig for you, maybe it will help
```

eth0   Link encap:Ethernet  HWaddr 00:50:DA:1F:96:7B
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe1f:967b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:631501 (616.7 KiB)  TX bytes:202697 (197.9 KiB)
          Interrupt:11 Base address:0xd000

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1677405 (1.5 MiB)  TX bytes:1677405 (1.5 MiB)


``` 

I've DHCP on,
That was it so far

Thanks anyway

Flip
The Netherlands

---

### Post by tonym on 2005-08-15
Has /etc/networking/interfaces got a line 

auto eth0

before the iface line?  If not try adding one.

If that doesn't work post the contents of /etc/networking/interfaces

and the results of calling 

route

---

### Post by +Flip on 2005-08-16
[QUOTE=tonym]Has /etc/networking/interfaces got a line 

auto eth0

before the iface line?  If not try adding one.

If that doesn't work post the contents of /etc/networking/interfaces

and the results of calling 

route[/QUOTE]
 It didn't have the auto eth0 line. I added it. Now i'm going to reboot!

```

root@Fubuntu:/etc/network # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         CO106883-b      0.0.0.0         UG    0      0        0 eth0
root@Fubuntu:/etc/network #

```

---

### Post by +Flip on 2005-08-16
It still doens't work

Here is my /etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.101
netmask 255.255.255.0
gateway 192.168.2.1

```

---

