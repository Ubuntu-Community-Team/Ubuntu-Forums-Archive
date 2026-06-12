---
title: "firewall with webmin help"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by ulao on 2007-10-10
Hello all, Setting up my ubuntu server to replace my good old libranet server as the author is no longer with us. 

Currently I need a bit of help with my nat/firewall.  I used the built in libranet firewall previously trouble free. 

Here is my dhcp config with virtual eth0:1
```


root@spawnubuntu:~# vi /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
address 192.168.0.18
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
dns-nameservers 65.32.5.74
#pre-up iptables-restore < /etc/iptables.up.rules
~

```

Basically I just need a solid method to nat from one to the next.. I set up shorwall with webmin, and I cant get shorwall nor linux firewall to work right.. Looking at the two the linux fire wall looks a bit easier to set up.

Packets before routing (PREROUTING)
Select all. | Invert selection.

Action 	Condition 	Move 	Add
Accept 	If input interface is eth0:1


Outgoing packets (OUTPUT)
Select all. | Invert selection.

Action 	Condition 	Move 	Add
Accept 	If output interface is eth0

Packets after routing (POSTROUTING)
Select all. | Invert selection.

Action 	Condition 	Move 	Add
Accept 	If output interface is eth0:1


I tried a lot of combinations wit no luck, this is my current.  I dont mind what I use if any one has a suggestion, and I'm not partial to webmin. Any help is appreciated.

---

### Post by ulao on 2007-10-10
looks like this did the trick..

modprobe iptable_nat
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

---

