---
title: "How to setup IP address, gateway and nameserver via CLI?"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by mahy on 2006-11-03
Hi y'all,

up till now i was using dhcp to get networking done, but no more. What i'd like is some help in setting up all the TCP/IP parameters, i.e. IP address, netmask, gateway and DNS server(s)... Thanks for any advice.

Mahy

---

### Post by dbott67 on 2006-11-03
The command would be something like:
```

sudo ifconfig ethX <IP> netmask <mask> broadcast <bcast>
```
```

sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0 broadcast 192.168.1.255
```

For the name server, you can edit the /etc/resolv.conf file and add the following:
```
nameserver <IP_Address>
```
```
nameserver 192.168.1.1
```

-Dave

---

### Post by mahy on 2006-11-03
Thanks a lot!

I guess i can use

echo "nameserver 0.0.0.0" >> /etc/resolv.conf

coz i need to make a script.

---

### Post by dbott67 on 2006-11-03
echo will work.  You *may* want to use just a single > to overwrite the /etc/resolv.conf, rather than append to the end, just in case there is something in there (maybe mv resolv.conf --> resolv.conf.bak first)

For the gateway, you need to use the **route** command.

Use **route -n** to display current routing table (this is mine, so it's already got the gw from DHCP):
```
dbott@thedrake:~$ route -n
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
[COLOR="Red"]0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0[/COLOR]

```

The 0.0.0.0 entry will be missing in yours.  To add a new default gateway off of the 192.168.1.0 network:
```
route add -net default gw 192.168.1.1 dev eth0
```

**man route** for all of the particulars.

-Dave

---

