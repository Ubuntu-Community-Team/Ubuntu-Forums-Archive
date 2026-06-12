---
title: "Networking from XP to ubuntu server 6.10"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by Bill007 on 2006-11-22
Well here goes again Sorry lloyd_b and trubblemaker Im back

**Mission**

To find my newly installed Ubuntu Server 6.10 Box from my remote XP WINDBLOWS box

I have two network cards In the server

eth0  dhcp (working on the net fine Phew)
eth1 static (dont know what the heck its doing](*,) )


**sudo nano /etc/network/interfaces** has been configured to

auto lo
iface lo inet loopback

mapping hotplug
script grep
map eth0

#the primary network interface

inface eth0 inet dhcp


auto eth1
iface eth1 inet static
address 192.168.2.100
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255

to set the new settins I did

**sudo ifdown eth1**

**sudo ifup eth1**



**sudo ifconfig |more** says


eth0 

Link encap:Ethernet HWaddr 00:E0:4C:E9:39:F7
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr:fe80::2e0:4cff:fee9:39f7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3365 (3.2 KiB) TX bytes:1026 (1.0 KiB)
Interrupt:185 Base address:0xa000



eth1 

Link encap:Ethernet HWaddr 00:14:85 5:18:6F
inet addr:192.168.2.100 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr:fe80::214:85ff:fed5:186f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4425 (4.3 KiB) TX bytes:0 (0.0 B)
Interrupt:193 Base address:0xc400


lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 KiB) TX bytes:0 (0.0 KiB)

I have installed webmin 1.307  so this is what Im trying to communicate with in a remote situation

Help going mental in New Zealand:twisted: 

Thanks in advance

---

### Post by ingo on 2006-11-22
not sure what you'd do from windowze, but from linux the following should do:

ssh -X your_username@192.168.1.5

and Bob's your uncle :)

---

### Post by Bill007 on 2006-11-22
Hmmmm not sure what that will do

I need to set up webmin from a remote networked box running windblows XP or al least be able to see the server some how from another location
:???:

---

### Post by ingo on 2006-11-22
> **Bill007 said:**
> **Mission**

To find my newly installed Ubuntu Server 6.10 Box from my remote XP WINDBLOWS box

Ah, I was suggesting that you open a secure remote shell on your windowze machine and access your server that way. Not sure about webmin, never used it. But a secure shell with the -X function allows you to run X remotely, so you should be ok. VPN is also relatively simple and platform independent I believe...

Best of luck anyway:)

---

### Post by Bill007 on 2006-11-22
Thanx ingo

I guess that learning curve is steep at the begining

Im trying to work from the command line and have learnt a lot but this networking has got me scratching my head

I  here samba being used alot(to talk to windows) is this more to do with the Graphical side of things

Appreciate your help anyways 

Its Lonely in between Box's

Regards Bill007

---

### Post by ingo on 2006-11-22
have a google for xp and vpn, there must be tons of stuff out there. once you know how to do it open krfb... doh!!! I'm using kubuntu, so no use to you! 

But a quick forum search for vpn should help you along the way...

I use vpn in my network. Basically it means that I control my desktop from my old IBM TP600E while chilling in bed (which is nice). 

Samba is a different thing entirely. Here you share some directories or printers, but not the whole machine. Probably best to google samba for that cos its distro independent.

---

### Post by Bill007 on 2006-11-22
Hey thanks Again ingo Chillin in bed is a great Idea ill just have to dream about controlling my Machine from a far, but I do feel a little closer then before  thanks for the tip on vpn I will not give up  

all I want right now is to see the ubuntu box on the LAN network 

when i stitch this all together I will post for all Ubuntu network newbies like me just as well I dont have to work for  a living cause this is hogging my time

Over and out

---

