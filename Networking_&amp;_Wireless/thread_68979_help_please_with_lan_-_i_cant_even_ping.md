---
title: "help please with lan - i cant even ping"
date: 2005-09-24
forum: Networking &amp; Wireless
---

### Post by nephish on 2005-09-24
hey there,
i had to move my computers and make the router the client and vice versa.
the router needs to be my ubuntu box, my client is Arch linux.

i get the internet through ppp0 (adsl) set up on eth1
my other network card is connected to the other computer via crossover cable. 

i installed firestarter, set it up in the gui with internet connection sharing with ppp0 being the incomming and sharing to lan on eth0

i had done a ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

the other computer is set up with eth0 static ip of 192.168.1.2
i cannot even ping the other computer.

here is my ifconfig on the router (ubuntu) computer
```

eth0      Link encap:Ethernet  HWaddr 00:50:BF:93:D0:81
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe93:d081/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:360 (360.0 b)  TX bytes:1818 (1.7 KiB)
          Interrupt:11 Base address:0x1000

eth1      Link encap:Ethernet  HWaddr 00:09:5B:E1:7E:BA
          inet6 addr: fe80::209:5bff:fee1:7eba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32889728 (31.3 MiB)  TX bytes:1113507 (1.0 MiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1636537 (1.5 MiB)  TX bytes:1636537 (1.5 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:63.97.189.238  P-t-P:63.97.189.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:22619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:32384910 (30.8 MiB)  TX bytes:785691 (767.2 KiB)

```

and here is what i get with route
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
63.97.189.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         63.97.189.1     0.0.0.0         UG    0      0        0 ppp0

```



the first line of ifconfig on the Arch linux box (the client) is
```

192.168.1.2 Bcast 192.168.0.255 Mask 255.255.255.0

```

oh dear, can someone please help with this stuff?

i have ipmasq installed. i have a 1 in /proc/sys/net/ipv4/ip_forward
in firestarter i have 'allow 192.168.1.2' to connect


dont know what else i am doing wrong.

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=nephish]hey there,
i had to move my computers and make the router the client and vice versa.
the router needs to be my ubuntu box, my client is Arch linux.

i get the internet through ppp0 (adsl) set up on eth1
my other network card is connected to the other computer via crossover cable. 

i installed firestarter, set it up in the gui with internet connection sharing with ppp0 being the incomming and sharing to lan on eth0

i had done a ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

the other computer is set up with eth0 static ip of 192.168.1.2
i cannot even ping the other computer.

here is my ifconfig on the router (ubuntu) computer
```

eth0      Link encap:Ethernet  HWaddr 00:50:BF:93:D0:81
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe93:d081/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:360 (360.0 b)  TX bytes:1818 (1.7 KiB)
          Interrupt:11 Base address:0x1000

eth1      Link encap:Ethernet  HWaddr 00:09:5B:E1:7E:BA
          inet6 addr: fe80::209:5bff:fee1:7eba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32889728 (31.3 MiB)  TX bytes:1113507 (1.0 MiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1636537 (1.5 MiB)  TX bytes:1636537 (1.5 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:63.97.189.238  P-t-P:63.97.189.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:22619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:32384910 (30.8 MiB)  TX bytes:785691 (767.2 KiB)

```

and here is what i get with route
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
63.97.189.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         63.97.189.1     0.0.0.0         UG    0      0        0 ppp0

```



the first line of ifconfig on the Arch linux box (the client) is
```

192.168.1.2 Bcast 192.168.0.255 Mask 255.255.255.0

```

oh dear, can someone please help with this stuff?

i have ipmasq installed. i have a 1 in /proc/sys/net/ipv4/ip_forward
in firestarter i have 'allow 192.168.1.2' to connect


dont know what else i am doing wrong.[/QUOTE]
Looks good to me.  Is the other computer running a firewall?  Are the routes configured correctly on the other PC?  If you disable the ppp0 interface, are you able to ping, then?

---

### Post by nephish on 2005-09-25
[QUOTE=cwaldbieser]Looks good to me.  Is the other computer running a firewall?  Are the routes configured correctly on the other PC?  If you disable the ppp0 interface, are you able to ping, then?[/QUOTE]
 if i disable the ppp0 interface wont i loose the internet connection?

---

### Post by Orborde on 2005-09-25
[QUOTE=nephish]if i disable the ppp0 interface wont i loose the internet connection?[/QUOTE]
Yes, but right now you're just testing to see if your two computers are talking to one another, not the Internet.

You could try having each computer attempt to ping itself, but using its network address as the ping target instead of 127.0.0.1. This might tell you whether it's firewalled or something.

---

### Post by nephish on 2005-09-25
[QUOTE=Orborde]Yes, but right now you're just testing to see if your two computers are talking to one another, not the Internet.

You could try having each computer attempt to ping itself, but using its network address as the ping target instead of 127.0.0.1. This might tell you whether it's firewalled or something.[/QUOTE]
 ok, i used the ubuntu live cd on the client and was able to get the internet, but by ip addresses only.. the dns was not working. i was using the same dns servers that the router (ubuntu ) computer was using. should i use the ubuntu computers ip as the dns server? 
i e 
nameservers
search 192.168.1.1 ?

i will giver a try this morning.
thanks for your help with this.

---

