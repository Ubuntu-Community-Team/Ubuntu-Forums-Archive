---
title: "DHCP problem and boot problem"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by jupiter1 on 2010-10-17
So there are 2 main problem that I have after installation Ubuntu Server 10.10:

1. DHCP client is not receive configuration. tried to configure /etc/dhcp3/dhclient.conf with my client-id(MAC) but this didn't work.

2. Booting from cd/dvd also already doesn't work. Wanted to install different OS but it fails. Cd burned correctly and md5 checked successful - also checked it on the other computer.

What can I do in thi situation? please help :)

---

### Post by spikoley on 2010-10-17
1.  Run the *dhclient* command and post the results if it doesn't work.  Also, post the result of ifconfig.

```
sudo dhclient
```
```
sudo ifconfig -a
```

2.  Did you change the BIOS to boot from USB first?

---

### Post by Fiable.biz on 2010-10-20
Hello.

I don't understand very well jupiter1's first problem, but ours may be similar. We have a PPPoE internet access with dynamic allocation of a private IP. We are inside a big LAN, of the size of the city. We used to connect through a modem and a switch, so only one computer at a time could have internet access, configured by "pppoeconf" and lauched by "pon" (On Mandriva Linux, there is a graphical tool for this, but I couldn't find any on Ubuntu.)
We've just replaced the switch by a router, configured it to provide DHCP service with fix IPs for our computers (I would have chosen static IPs, but If I do that, it seems I have to provide DNS IPs etc. by hand, and the experience proves that when Telecom Mongolia changes this kind of things, they don't warn, so it's wiser to get them dynamically.), and said politely to "pppoeconf" not to start at boot. But dhclient doesn't start at boot for that. When I launch it by hand, I have the net. **I'd like the internet connection to start at boot** when available. This is a notebook, so sometimes it's just not connected, sometimes it uses Wifi.
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:b3:7a:eb:8e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:22 erreurs:0 :0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:2871 (2.8 KB) Octets transmis:2871 (2.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:e1:68:d8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

```
```
$ ping 192.168.1.1
connect: Network is unreachable

```
```
$ sudo dhclient
[sudo] password for henri: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFFLAGS: Unknown error 132
SIOCSIFFLAGS: Unknown error 132
Listening on LPF/wlan0/00:1f:3c:e1:68:d8
Sending on   LPF/wlan0/00:1f:3c:e1:68:d8
Listening on LPF/eth0/00:25:b3:7a:eb:8e
Sending on   LPF/eth0/00:25:b3:7a:eb:8e
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 2147483648 seconds.

```And now
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:b3:7a:eb:8e  
          inet adr:192.168.1.103  Bcast:255.255.255.255  Masque:255.255.255.0
          adr inet6: fe80::225:b3ff:fe7a:eb8e/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2 erreurs:0 :0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:767 (767.0 B) Octets transmis:3549 (3.5 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:22 erreurs:0 :0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:2871 (2.8 KB) Octets transmis:2871 (2.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:e1:68:d8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

```
Hum... This is Frenglish. "Boucle" means "Loop", "Octet" means "Byte" and "reçus" means "received". I hope the other French words are understandable.
Note that, on Mandriva, DHCP starts at boot. I didn't even need to uninstall the direct PPPoE connection. In fact, I made absolutely no change on Mandriva: as soon as I had given to the router the MAC addresses of Mandriva computers and the IP numbers to provide them then rebooted the router, it just worked.

---

### Post by cariboo on 2010-10-21
> 2. Booting from cd/dvd also already doesn't work. Wanted to install different OS but it fails. Cd burned correctly and md5 checked successful - also checked it on the other computer.

Could you describe what the problem is? Does your system not boot at all? Does it boot but stop at the plymouth screen? Does it boot to a black screen?

---

