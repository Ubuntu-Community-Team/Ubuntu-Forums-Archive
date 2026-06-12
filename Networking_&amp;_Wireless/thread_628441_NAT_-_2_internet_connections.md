---
title: "NAT - 2 internet connections"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by bzzz on 2007-12-01
Hello.
I have a router (ubuntu 7.04 installed) with 3 network cards and 2 broadband internet connections. I also have a VLAN capable switch. On eth1 and eth2 are the the internet connections (since i can't tag a port on my switch) and on eth4 i have vlans 21 and 23. I want to separate two lans and every lan with it's own connection. I managed to make a iptables script and the internet works on both lans, but the problem is that all the computers (from both connections) are accessing the internet via one internet connection.

Here is my iptables script:
```

#!/bin/bash

IP_EXTERN_CLIENTI="88.xxx.219.0"
IP_EXTERN_HORAJOS="88.xxx.219.3"

CLASA_INTERN_CLIENTI="192.168.1.0/24"
CLASA_INTERN_CLIENTI2="192.168.4.0/24"

IFACE_EXTERN_CLIENTI="eth1"
IFACE_INTERN_CLIENTI="eth4.21"
IFACE_EXTERN_CLINEIT2="eth2"
IFACE_INTERN_CLIENTI2="eth4.23"

IPTABLES="iptables"

# MISC
iptables -t nat -F
iptables -F

# SNAT
iptables -t nat -A POSTROUTING -o $IFACE_EXTERN_CLIENTI -j SNAT --to $IP_EXTERN_CLIENTI # R1
iptables -t nat -A POSTROUTING -o $IFACE_EXTERN_CLIENTI2 -j SNAT --to $IP_EXTERN_CLIENTI2 # R2

# DNAT
iptables -t nat -A PREROUTING -i $IFACE_EXTERN_CLIENTI -j DNAT --to $IP_EXTERN_CLIENTI #R1
iptables -t nat -A PREROUTING -i $IFACE_EXTERN_CLIENTI2 -j DNAT --to $IP_EXTERN_CLIENTI2 #R2

```
Now, both lans are accessing the internet with pe .3 IP Address (if you're asking why 88.xxx.219.0, the answer is that my ISP has a agregated class). Where I'm doing it wrong? Please help me.

Thanks and please excuse my english.

---

### Post by bzzz on 2007-12-01
Heh, i made it (actualy someone helped me). I'll post the solution if someone needs it sometime.
create 2 iproute tables
```

echo 1 conex1 >> /etc/iproute2/rt_tables
echo 2 conex2 >> /etc/iproute2/rt_tables

```
rules for conex1
```

ip route add default 88.xxx.216.1 dev eth1 table conex1
ip rule add from 192.168.1.0/24 table conex1

```
and for table conex2
```

ip route add default via 88.xxx.216.1 dev eth2 table conex2
ip rule add from 192.168.4.0/24 table conex2

```
and how the nat
```

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -j SNAT --to-source 88.xxx.219.0
iptables -t nat -A POSTROUTING -s 192.168.4.0/24 -j SNAT --to-source 88.xxx.219.3

```

---

