---
title: "Need help configuring two network cards"
date: 2016-05-26
forum: Networking &amp; Wireless
---

### Post by Andrew_Hobson on 2016-05-26
Hello,

I would need some help to configure two network cards for an Ubuntu machine. The system is ubuntu 14.04 LTS.

I have the regular internal network interface and I added an extra network interface.

The machine is used to host a webserver.

The objective is to give access to this webserver to 2 different networks.
My internal network on one interface
Our external network on the second interface

And I am unable to make this happen.

Can someone please help me out with this configuration?  It would be very nice ;-)

Thank you and best regards.

Andrew

---

### Post by TheFu on 2016-05-26
Please post the exact, current configuration and the configuration you want. Use 
* route
* ifconfig
please and "code tags" so the output lines up properly.
Also, need to know where the router(s) are (IP and netmask).

---

### Post by Andrew_Hobson on 2016-05-26
Hello,

I just noticed that the new network card is displayed as "Cable Disconnected"... But it's not true, the leds are on and the network cable is connected.

The card is an INTEL Pro/1000 GT Desktop Adapter. And is showing up as such in the dropdown network menu.

Here is the outpu for route :

```

Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
default         10.192.120.1    0.0.0.0         UG    0      0        0 eth0
10.192.120.0    *               255.255.254.0   U     1      0        0 eth0

```

Here is the output for ifconfig :

```

eth0      Link encap:Ethernet  HWaddr 00:0f:fe:92:3e:6b
          inet adr:10.192.120.12  Bcast:10.192.121.255  Masque:255.255.254.0
          adr inet6: fe80::20f:feff:fe92:3e6b/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:42952 erreurs:0 :0 overruns:0 frame:0
          TX packets:24600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:27395229 (27.3 MB) Octets transmis:13582835 (13.5 MB)
          Interruption:19 Mémoire:f0500000-f0520000

eth1      Link encap:Ethernet  HWaddr 90:e2:ba:c4:bd:a6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

lo        Link encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:2148 erreurs:0 :0 overruns:0 frame:0
          TX packets:2148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:237190 (237.1 KB) Octets transmis:237190 (237.1 KB)

```

Guess the first thing is to make this eth1 network active ;-)

Thanks for the help.

Andrew

---

### Post by TheFu on 2016-05-26
Hope the leads helped. 

Please use **code tags**, not *quotes* in the next post.  Things will line up and be much more readable for helpers that way. Easier to read will get more people looking.

---

### Post by Andrew_Hobson on 2016-05-27
Hello again,

Need your help to activate this network card. For me it must work because the leds are on. But the lnk=no...

Can you help me?

---

### Post by TheFu on 2016-05-27
Thanks for the code tags.

Did you configure eth1 manually?  /etc/network/interfaces is the file for that, plus for non-standard setups, eth0 needs to be manually configured too. Same file.
Can't say anything more, since my first questions haven't been answered yet.

---

### Post by Andrew_Hobson on 2016-05-27
No I didn't configure manually. I used the graphical interface of ubuntu.

so here is the content of the /etc/network/interfaces file :

> 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


What didn't I reply yet to your first questions ?

Thanks.

Andrew

---

### Post by TheFu on 2016-05-27
>     Please post the exact, current configuration and the configuration you want.
and
> Also, need to know where the router(s) are (IP and netmask). 

We know what you have, but not what you want or how the rest of the network is architected.

---

### Post by Andrew_Hobson on 2016-05-27
I'm afraid of putting on the net some sensible data. May I give you thru private message my config ?

Hello,

I got my second network card up and going. So here is the output for ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:0f:fe:92:3e:6b
          inet adr:10.192.120.12  Bcast:10.192.121.255  Masque:255.255.254.0
          adr inet6: fe80::20f:feff:fe92:3e6b/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4360 erreurs:0 :0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:575794 (575.7 KB) Octets transmis:99284 (99.2 KB)
          Interruption:19 Mémoire:f0500000-f0520000

eth1      Link encap:Ethernet  HWaddr 90:e2:ba:c4:bd:a6
          inet adr:193.134.217.134  Bcast:193.134.217.159  Masque:255.255.255.22                                                                               4
          adr inet6: fe80::92e2:baff:fec4:bda6/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:73 erreurs:0 :0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:5586 (5.5 KB) Octets transmis:9321 (9.3 KB)

lo        Link encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:309 erreurs:0 :0 overruns:0 frame:0
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:43948 (43.9 KB) Octets transmis:43948 (43.9 KB)
```

And for route:

```
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
default         10.192.120.1    0.0.0.0         UG    0      0        0 eth0
10.192.120.0    *               255.255.254.0   U     1      0        0 eth0
193.134.217.128 *               255.255.255.224 U     1      0        0 eth1
```

What do you need more to help me? My objective is to be able to access the webpage from these 2 addresses : 193.134.217.134 or 10.192.120.12

Thanks for the help.

Andrew

---

