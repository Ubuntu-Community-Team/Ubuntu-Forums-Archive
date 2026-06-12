---
title: "Can Windows block other computers in a Network?"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2008-04-30
I have a question:

Me and my brother live in the same building, but on a different floor.
We share a ADSL internet connection. 

Because he is 5 etages below me, and because the WLAN has not this range, I connect to the router via PowerLine.
Normally this works well.

Unfortunately he uses Windows and is unwilling to switch to Linux.
Now, whenever he opens MS-Outlook, the whole network gets blocked for me.
I cannot open any Website, pinging any computer in the internet timeouts, and i cannot even reach the router at 192.0.0.1 ...

As soon as he closes Outlook, I can again access everything, ping anyting and I reach the router. Unfortunately, he writes E-Mails for hours, and using OutlookExpress instead of Outlook leads to the same result.
On the other hand, browsing the Web at the same time works flawlessly.

Now the good question: Is there anything **I** can do against this (since he's not willing to do anything...)?

I already tried configuring the network to use a static IP instead of getting the IP via DHCP, but although using a static IP does work, it doesn't help against MS-Outlook...

---

### Post by ivze on 2008-04-30
Does he has a good antivirus? If doesn't, download some free scanner and ask him make a scan (e.g., this [ftp://ftp.drweb.com/pub/drweb/cureit/cureit.exe](ftp://ftp.drweb.com/pub/drweb/cureit/cureit.exe)). The behaviour, is obviously, very strange.

---

### Post by WitchCraft on 2008-04-30
> **ivze said:**
> Does he has a good antivirus? If doesn't, download some free scanner and ask him make a scan (e.g., this [ftp://ftp.drweb.com/pub/drweb/cureit/cureit.exe](ftp://ftp.drweb.com/pub/drweb/cureit/cureit.exe)). The behaviour, is obviously, very strange.

He has Kaspersky AV, and I don't think it's a virus.

---

### Post by ivze on 2008-04-30
Kaspersky is a good one. I hope here will come other people, that have ideas of what's up with the Microsoft black-box. :)

---

### Post by SpaceTeddy on 2008-04-30
How exactly is the connection setup ? how do you guys connect ? do you share an internal network and use your bro's as a gateway ? do you use a proxy ? some gateway software ?

please help me understand some more of the setup so i can try to help you :)

---

### Post by WitchCraft on 2008-04-30
> **SpaceTeddy said:**
> 
How exactly is the connection setup ? 
how do you guys connect ? 
do you share an internal network and use your bro's as a gateway ? 
do you use a proxy ? 
some gateway software ?

please help me understand some more of the setup so i can try to help you :)


eth0 is the wired LAN I'm using, eht1 is Wireless
```

root@all:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:69:49:e2  
          inet addr:192.168.0.33  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe69:49e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:324197053 (309.1 MB)  TX bytes:13203348 (12.5 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:ad:53:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:78062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x8000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70775 (69.1 KB)  TX bytes:70775 (69.1 KB)

root@all:~# 

```

From the modem:
```

IP-Address 83.78.137.149
IP-Gateway 83.78.128.1
Primary Name-Server 195.186.1.108 cns3.bluewin.ch
Alternative Name-Server 195.186.4.108 cns4.bluewin.ch
Speed: 3072/256 (kbps)
Line loss: 9/6 dB
VPI: 8
VCI 35
Protocoll PPP over Ethernet LLC/SNAP
Bridging: deactivated
Simultaneous Bridging/Routing: deactivated
UPnP: Yes
Router IP-Address:      192.168.0.1
Subnet mask: 	        255.255.255.0
DHCP-Start adress: 	192.168.0.33
DHCP-End address: 	192.168.0.63
DHCP-Allocation time:   3 minutes
DHCP-Server on: 	yes
WAN IP Address:         83.78.137.149
IP-Forwarding:          off
NAT:                    on
User defined NAT freed Services:     Quake3, Server, 192.168.0.33
VLAN 1-16:              off, port based
Timezone:               GMT + 1, Central Europe
Priority of Services:   on
Ratio of low to high priority: 92
User defined priority services: none


IP-Interfaces
Address 	Network mask 	Name
192.168.0.1 	255.255.255.0 	Ethernet 100BT
83.78.137.149 	0.0.0.0 	WAN vcc1

Network-Routing-Tabele
Network Target 	Networkmask 	Gateway 	Interface
0.0.0.0 	0.0.0.0 	83.78.128.1 	WAN vcc1
192.168.0.0 	255.255.255.0 	192.168.0.1 	Ethernet 100BT

Host-Routing-Tabele
Network Target 	Network mask     	Gateway 	Interface
127.0.0.1 	255.255.255.255 	127.0.0.1 	Loopback
83.78.128.1 	255.255.255.255 	83.78.128.1 	WAN vcc1
192.168.0.1 	255.255.255.255 	192.168.0.1 	Ethernet 100BT
192.168.0.255 	255.255.255.255 	255.255.255.255 Ethernet 100BT


```

Powerline LAN:
```

Manufacturer: devolo
Product:      dLAN Ethernet
Version:      HighSpeed 85
Content: 2 Highspeed Ethernet adapters for data transmission in the house-intern electricity network 
System requirement: Windows 98/ME/2000/XP, Mac OS X, Linux
Software: devolo Informer, devolo easyShare, devolo EasyClean

Transmission speed: 85 Mbit/s
Range: 200 m
Encryption: DES-pro Encryption

```

Network setup:
[IMG]http://img138.imageshack.us/img138/9634/dlan200avdeskpcinternetuc8.png[/IMG]

Traceroute:
```

root@all:~# tracert www.ubuntuforums.org
traceroute to www.ubuntuforums.org (91.189.94.186), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  6.837 ms  6.865 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * i79zhb-015-vla200.bb.ip-plus.net (138.187.129.62)  14.843 ms  19.734 ms
 7  i00ffm-015-xxx2-1.bb.ip-plus.net (138.187.130.126)  30.515 ms  35.867 ms  45.808 ms
 8  ge0-1-0-cr0.ixf.de.as6908.net (80.81.192.244)  63.554 ms * *
 9  * * *
10  * * *
11  * * gw0-0-gr.canonical.com (91.189.88.10)  37.797 ms
12  ohiggins.canonical.com (91.189.94.186)  43.722 ms  33.015 ms *
root@all:~# 

```

Info for hackers: the WAN IP is a dynamic IP. I've now changed it ;-)

> **SpaceTeddy said:**
> 
How exactly is the connection setup ? how do you guys connect ? 

Answered by the above info.

> **SpaceTeddy said:**
> 
do you share an internal network and use your bro's as a gateway ? 

Yes. The gateway is not my brothers PC, but the router, which is in my brother's room.
So it's not necessary for his PC to run for me to be able to go into the internet.

> **SpaceTeddy said:**
> 
Do you use a proxy ? 

No.

> **SpaceTeddy said:**
> 
some gateway software ?

No.

---

### Post by SpaceTeddy on 2008-05-01
wow - thank you for that answer. very nice :)

unforteuantly, it also destroys all my hope of being able to help you - your setup looks perfect, and your computer should in no way be affected by the your brothers in this setup... 

since your router dials in and you two share a normal ip subnet, it should not be possible to for one computer to block the other entirely. It just does not make sense.

The only possible scenario (i can think of) where your brothers computer destroys your internet is that when he starts outlook, it dials itself in a second time. This would mean the router gets kicked out of the internet, as it is forced to go from being a router to being a modem for your brother. As soon as he closes outlook the connection is terminated and the router dials in itself again. 

This is a *very* long shot. i don't even know it this is possible or not ! but it's the only thing i could think of that could be causing such a behaviour.

I'd suggest you go through the connection settings in your brothers computer and make sure there is no dial-in set nowhere (not in browser, not in outlook or anywhere else).

Otherwise i can only think of tests to run. For example, when your internet gets cut, can you still ping/access the router. Does the router still have an external ip then ? what ip's does your brothers computer have he opens outlook ? what routes are set ?

i know, more questions... i'm just trying to help :)

---

### Post by WitchCraft on 2008-06-21
> **SpaceTeddy said:**
> 

I'd suggest you go through the connection settings in your brothers computer and make sure there is no dial-in set nowhere (not in browser, not in outlook or anywhere else).

Otherwise i can only think of tests to run. For example, when your internet gets cut, can you still ping/access the router. Does the router still have an external ip then ? what ip's does your brothers computer have he opens outlook ? what routes are set ?

i know, more questions... i'm just trying to help :)

there is no dial-in, it's ADSL via LAN, and dial-in is not set, not in the browser, nor in outlook nor in network settings.

Yes, the router has the external IP, not the computers in the network, they have a 192.* IP.

My brother's IP strangely changes to 169.* when he opens Outlook.

I just had a thought: could that possibly be Kaspersky Anti-Virus that blocks ? (so called hacker protection...)

It does still not work when I deactivate Kaspersky, but when I think back, I think the problems started after he installed Kaspersky...

---

### Post by WitchCraft on 2008-06-24
bump

---

