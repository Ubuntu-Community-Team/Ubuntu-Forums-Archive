---
title: "In need of help"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by sambtravis on 2006-08-25
I built a custom computer. After i put ubuntu on it my networking card isn't working. It worked in windows and in live CD before installing. My moterboard is an MSI K9N Neo-F Socket AM2 NVIDIA nForce 550. Help would be most appreciated.](*,)

Or if AM2 and nForce 550 is a lost cause for a while on ubuntu what would be good to switch to till support is better for my chipset? I'm still a linux newbie so nothing too terminal intensive.

---

### Post by apjone on 2006-08-25
have you configured the card? do you get any errors?

---

### Post by The_Artist on 2006-08-25
Type ifconfig in the terminal and give us the output please...

---

### Post by sambtravis on 2006-08-27
ok ifconfig gives me an output of

link encap: ethernet  HWaddr  00.16.17.72.8d.6e
up broadcast multicast   MTU: 1500   Metric: 1
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen: 1000
RX bytes:0 (0.0b)   TX bytes:0 (0.0 b)
interrrupt: 225 Base address: 0x2000

this is transcribed so there might be some CAP errors but everything else is correct

---

### Post by The_Artist on 2006-08-27
A working card must output sthg like that :

```
eth0      Lien encap:Ethernet  HWaddr 00:30:1B:B0:1C:A2
          inet adr:192.168.0.249  Bcast:255.255.255.255  Masque:255.255.255.0
          adr inet6: fe80::230:1bff:feb0:1ca2/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:6929 erreurs:0 :0 overruns:0 frame:0
          TX packets:6642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:4876201 (4.6 MiB) Octets transmis:569354 (556.0 KiB)
          Interruption:11 Adresse de base:0x2000

```

1. Please confirm me that you have somrthing like "eth0" that appears in the margin, and that you don't have rewritten

In this case, that means like the card seems to be identified, because the mac adress is present (HWaddr)

2. My first impression is that this card doesn't success obtaining an ip adress. Curious because it works with the live CD you says... Maybe this can be a setup problem with your router, or a dhcp client setting to do on you machine...

a. Could you tell us more about the way you use to connect to the network ? a router ? an adsl modem ? do you know the gateway and so and so ?

b. Could you type the output of (replace eth0 with the name of your interface, see 1 above) :

```
angelo@shuttle:~$ sudo ifdown eth0
angelo@shuttle:~$ sudo ifup eth0
```

Good luck ;)

---

### Post by sambtravis on 2006-08-27
My router is a linksys WRT54Gv5 and my modem is a motorola surfboard model #sb5100

my connection is indeed titled eth0 i just forgot to type it.

when typing ifdown eth0 it gives me an output of:
Internet Systems Consortium DHCP Client v3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All Rights Reserved.
for info please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:17:72:8d:6e
Sending on LPF/eth0/00:16:17:72:8d:6e
sending on Socker/fallback

when typing ifup eth0 it gives me an output of:
Internet Systems Consortium DHCP Client v3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All Rights Reserved.
for info please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:17:72:8d:6e
Sending on LPF/eth0/00:16:17:72:8d:6e
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping

---

### Post by The_Artist on 2006-08-28
OK, so these card doesn't success obtaining an IP adress...

Could you reboot with the live CD (working you said) and go to :
System > Administration > Network, and there edit "eth0" properties and note them...

Is it the same parameters than your hard drive install ? Try them if different...

---

### Post by sambtravis on 2006-08-28
Ok i tried that last night and there were no differences... im probably just going to buy a new motherboard so i can actually OC it. A more proven mobo. But thanks for the help, i will probably be back when i get paid.

---

### Post by The_Artist on 2006-08-28
ok so you don't want to look further for a solution ?

---

### Post by larlin on 2006-08-29
I also have a MSI K9N board(the nForce 570 one) had the same thing network worked with live CD and not when installed, so I switched to the 64 bit version of ubuntu and there the network worked...

If I'm right guessing that this is a 64 bit system, try that...

larlin

---

### Post by orbital on 2006-08-29
I have the same problems with my network card. The card works fine when I boot to XP but with Ubuntu I'm having same problems getting the ip-address. Everything worked fine for months and suddenly today it doesn't work. What to do? I'm running Dapper.

---

