---
title: "Unable to configure large number of interfaces"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by UntakenUserName on 2006-08-30
I'm trying to run Ubuntu on a machine with ten eithernet interfaces.

I've had no trouble getting eth0 up:

```
still@attacker1:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:04:80:27  
          inet addr:192.168.99.130  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe04:8027/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7616 (7.4 KiB)  TX bytes:7763 (7.5 KiB)
          Interrupt:66 
```

I am able to browse the web etc, no problem.  However, I have two SUNHME 4 port cards in this machine and also another interface on the motherboard.  None of the rest of the interfaces work, and there's also a strange symptom; the interfaces get titled eth0, eth1 then eth10!  

Here's what I mean:
```
still@attacker1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:04:80:27  
          inet addr:192.168.99.130  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe04:8027/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9416 (9.1 KiB)  TX bytes:10183 (9.9 KiB)
          Interrupt:66 

eth1      Link encap:Ethernet  HWaddr 00:0F:1F:04:80:28  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:74 

eth10     Link encap:Ethernet  HWaddr 08:00:20:7A:E4:3C  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x6c00 

eth11     Link encap:Ethernet  HWaddr 08:00:20:C0:F8:01  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x6400 

eth12     Link encap:Ethernet  HWaddr 08:00:20:3F:AE:71  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x8000 

eth13     Link encap:Ethernet  HWaddr 08:00:20:33:D0:08  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x3800 

eth14     Link encap:Ethernet  HWaddr 08:00:20:FF:14:BB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0x2800 

eth15     Link encap:Ethernet  HWaddr 08:00:20:67:7A:65  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x3000 

eth16     Link encap:Ethernet  HWaddr 08:00:20:8B:33:58  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0x3c00 

eth17     Link encap:Ethernet  HWaddr 08:00:20:93:0B:DC  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x3400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:788 (788.0 b)  TX bytes:788 (788.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

And here's my interfaces file:

```
still@attacker1:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.99.130
netmask 255.255.255.0
gateway 192.168.99.254

iface eth1 inet static
address 192.168.98.130
netmask 255.255.255.0

iface eth2 inet static
address 192.168.97.130
netmask 255.255.255.0

iface eth3 inet static
address 192.168.96.130
netmask 255.255.255.0

iface eth4 inet static
address 192.168.95.130
netmask 255.255.255.0

iface eth5 inet static
address 192.168.94.130
netmask 255.255.255.0

iface eth6 inet static
address 192.168.93.130
netmask 255.255.255.0

iface eth7 inet static
address 192.168.92.130
netmask 255.255.255.0

iface eth8 inet static
address 192.168.91.130
netmask 255.255.255.0

iface eth9 inet static
address 192.168.90.130
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0
```

Of course I've tried:

```
still@attacker1:~$ sudo ifconfig eth1 up
Password:
still@attacker1:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0F:1F:04:80:28  
          inet6 addr: fe80::20f:1fff:fe04:8028/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:270 (270.0 b)
          Interrupt:74 

still@attacker1:~$ 
```

I did arrange the mac addresses as follows:

```
still@attacker1:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:1f:04:80:27 arp 1
eth1 mac 00:0f:1f:04:80:28 arp 1
eth2 mac 08:00:20:7a:8f:3c arp 1
eth3 mac 08:00:20:0e:9b:32 arp 1
eth4 mac 08:00:20:dc:2f:c8 arp 1
eth5 mac 08:00:20:61:b8:86 arp 1
eth6 mac 08:00:20:1a:c6:91 arp 1
eth7 mac 08:00:20:dc:ad:58 arp 1
eth8 mac 08:00:20:26:76:4a arp 1
eth9 mac 08:00:20:6c:c8:3d arp 1
```

I'm sure I'm overlooking something simple!  Thanks in advance for y'all's indulgence :mrgreen:

---

### Post by cylon359 on 2006-09-03
Well, the MAC addresses in your /etc/ifstab don't match your ifconfig output... So it thinks eth2 to eth9 are different cards, hence you're getting eth10 and up....

---

