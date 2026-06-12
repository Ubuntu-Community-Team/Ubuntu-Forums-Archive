---
title: "Using iptables as a router - problem"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by piedra96 on 2016-06-07
Hello all,

First at all, apologies for my English and thank you very much.

I'm new in iptables and I dont know exactly how it works.

I've got three virtual machines in VirtualBox:


[LIST=1]
[*]Debian (Connected to Internet with a bridged adapter and to the "Int1" network with an internal adapter)
[*]CentOS (Connected to "Int1" with an internal adapter and to the "Int2" network with another internal adapter)
[*]Ubuntu Servers (Connected to "Int2" with an internal adapter)
[/LIST]

I'm using iptables to access to the Internet, so my iptables configuration in Debian is the following one:


*[FONT=arial]$IPTABLES -A FORWARD -i $INET_IFACE -o $LAN_IFACE -j ACCEPT[/FONT]*
*[FONT=arial]$IPTABLES -A FORWARD -i $LAN_IFACE -o $INET_IFACE -j ACCEPT[/FONT]*
*[FONT=arial]# Masquerade[/FONT]*
*[FONT=arial]$IPTABLES -t nat -A POSTROUTING -s $LAN_IP_RANGE -o $INET_IFACE -j SNAT --to-source $INET_IP[/FONT]*

Where $INET_IFACE is the bridged adapter, the $LAN_IFACE is the internal adapter connected to "Int1" and $LAN_IP_RANGE is the IP of the "Int1" network.

CentOS has exactly the same configuration; but, in this case, $INET_IFACE is the internal network adapter connected to "Int1", the $LAN_IFACE is the internal network adapter connected to "Int2" and $LAN_IP_RANGE is the IP of the "Int2" network.


If I try a ping to google from the CentOS machine, it works; but if I do it from the Ubuntu Server, it doesnt work ](*,).

Any ideas? :confused:

Thanks again!

---

