---
title: "Ip address and subnet mask!"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by saspo on 2007-12-17
I am trying to install [FONT="Comic Sans MS"]_[SIZE="3"][COLOR="black"][COLOR="Red"]postgresql[[/COLOR][/COLOR]/SIZE]_[/FONT] and I have the following instructions (in red)

# Connections for all PCs on the subnet

# TYPE DATABASE USER IP-ADDRESS IP-MASK METHOD
host    all         all         [ip address]          [subnet mask]          md5

Which of the values below refers to the IP address and subnet mask.
Do I use info from[COLOR="Red"] "net lookup[/COLOR]" of from [COLOR="Blue"]eth0[/COLOR], or from [COLOR="Purple"]lo[/COLOR]

maadamos61@maadamos61-desktop:~$ net lookup maadamos61-desktop
[COLOR="Red"]127.0.1.1[/COLOR]
maadamos61@maadamos61-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:D6:E4:1E 
         [COLOR="MediumTurquoise"][COLOR="Blue"] inet addr:192.168.0.15  Bcast: 192.168.0.255  Mask:255.255.255.0[/COLOR][/COLOR]
          inet6 addr: fe80::20d:9dff:fed6:e41e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11341964 (10.8 MiB)  TX bytes:1265127 ( 1.2 MiB)
          Interrupt:17

lo        Link encap:Local Loopback 
         [COLOR="Purple"]inet addr:127.0.0.1  Mask:255.0.0.0[/COLOR]
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2431593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2431593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:292756973 (279.1 MiB)  TX bytes:292756973 (279.1 MiB)

---

### Post by wharp on 2007-12-17
I'm not familiar with the postgresql install, but I think you want the values from eth0.

---

### Post by mpokrywka on 2007-12-18
All depends what kind of database server you need. If postgresql will be used as database for local www server on the same machine then use only loopback address. If your database server should be accessible via network f.e. from other box with apache installed then use eth0 address.

My postgres config that is slightly edited default config from debian etch.
```

# TYPE  DATABASE    USER        IP-ADDRESS        IP-MASK           METHOD
# Database administrative login by UNIX sockets
local   all         postgres                                        ident sameuser
#
# All other connections by UNIX sockets
local   all         all                                             ident sameuser
#
# All IPv4 connections from localhost
host    all         postgres    127.0.0.1         255.255.255.255   ident sameuser
host    all         all         127.0.0.1         255.255.255.255   md5
#
# All IPv6 localhost connections
host    all         all         ::1               ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff        ident sameuser
host    all         all         ::ffff:127.0.0.1/128                ident sameuser
# allow connections to database from LAN (openoffice base)
host    all         all         192.168.7.0       255.255.255.0     md5
# reject all other connection attempts
host    all         all         0.0.0.0           0.0.0.0           reject

```

---

