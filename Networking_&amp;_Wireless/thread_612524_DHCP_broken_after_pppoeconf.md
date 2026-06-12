---
title: "DHCP broken after pppoeconf"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by emist on 2007-11-14
Hey guys,

I have a pretty strange issue I was hoping you could help me with. Ever since I ran pppoeconf in order to connect my fiesty box directly to the internet I haven't been able to obtain an ip from my router using dhcp. 

Whenever I try to run dhclient I get the following message. 

```


root@alpha:/home/emist# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:4d:4b:aa:89
Sending on   LPF/eth0/00:1a:4d:4b:aa:89
Can't bind to dhcp address: Address already in use
Please make sure there is no other dhcp server
running and that there's no entry for dhcp or
bootp in /etc/inetd.conf.   Also make sure you
are not running HP JetAdmin software, which
includes a bootp server.


```

DHCP was working literally minutes before and the only thing I could think of is maybe pppoeconf wrote some startup script that is running something that interferes with dhcp. However I haven't been able to find anything and im stuck. As of right now my feisty box has no way of getting to the net unless i want to lock the other 4 boxes out. This sucks =|

Im running feisty 64bit, if that helps. 

Help would be very welcome. =]

---

### Post by stevux on 2007-11-14
hrmmm looks like you've been a busy person, configging, installing, mucking about ..
are you running dhcp server perhaps?? if so, stop it, and try to restart the dhcp client

if not, can you send following output;
  'netstat -lnu'
  'ps -ef | grep dh'
  'cat /etc/network/interfaces'
  'dpkg --get-selections | grep -i dhc'

thx,

---

### Post by emist on 2007-11-15
Hey Steve,

Thanks for looking at the issue. 

Here is the output of the commands:

netstat -lnu:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
udp        0      0 0.0.0.0:640             0.0.0.0:*                          
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          
udp        0      0 0.0.0.0:641             0.0.0.0:*                          
udp        0      0 0.0.0.0:513             0.0.0.0:*                          
udp        0      0 0.0.0.0:1               0.0.0.0:*                          
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          
udp        0      0 0.0.0.0:32772           0.0.0.0:*                          
udp        0      0 0.0.0.0:32773           0.0.0.0:*                          
udp        0      0 0.0.0.0:517             0.0.0.0:*                          
udp        0      0 0.0.0.0:32774           0.0.0.0:*                          
udp        0      0 0.0.0.0:518             0.0.0.0:*                          
udp        0      0 0.0.0.0:7               0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 0.0.0.0:9               0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:666             0.0.0.0:*                          
udp        0      0 0.0.0.0:161             0.0.0.0:*                          
udp        0      0 0.0.0.0:162             0.0.0.0:*                          
udp        0      0 0.0.0.0:2727            0.0.0.0:*                          
udp        0      0 0.0.0.0:4520            0.0.0.0:*                          
udp        0      0 0.0.0.0:54321           0.0.0.0:*                          
udp        0      0 0.0.0.0:27444           0.0.0.0:*                          
udp        0      0 0.0.0.0:700             0.0.0.0:*                          
udp        0      0 0.0.0.0:66              0.0.0.0:*                          
udp        0      0 0.0.0.0:67              0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5060            0.0.0.0:*                          
udp        0      0 0.0.0.0:69              0.0.0.0:*                          
udp        0      0 0.0.0.0:4569            0.0.0.0:*                          
udp        0      0 0.0.0.0:474             0.0.0.0:*                          
udp        0      0 0.0.0.0:31335           0.0.0.0:*                          
udp        0      0 0.0.0.0:31337           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:111             0.0.0.0:*                          
udp        0      0 0.0.0.0:34555           0.0.0.0:*                          
udp        0      0 0.0.0.0:635             0.0.0.0:*                          
udp        0      0 169.254.6.235:123       0.0.0.0:*                          
udp        0      0 127.0.0.1:123           0.0.0.0:*                          
udp        0      0 0.0.0.0:123             0.0.0.0:*                          

```

There seems to be something on port 67(which i think is dhcp server?)
I don't know what its on it though.

ps -ef | grep dh:

```

root      4340     1  0 21:52 ?        00:00:00 /usr/sbin/dhcdbd --system
emist     5624  5028  0 21:54 pts/0    00:00:00 grep dh

```

maybe dhcdb is starting something?Not sure.

cat /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet ipv4ll

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

```

pre-up eth0? I should look into this after work tomorrow. 

dpkg --get-selections | grep -i dhc' didn't return anything. 

Thanks again for looking into the problem, i've been battling this thing for a few days now.

Take care.

---

### Post by emist on 2007-11-15
Hey, 

I edited out the pppoe stuff out of /etc/network/interfaces and rebooted and dhcp works now. Thanks a lot for the help =]

---

### Post by stevux on 2007-11-15
sometimes people need a push in the right direction, but self-help is the best help ...

thx,

---

