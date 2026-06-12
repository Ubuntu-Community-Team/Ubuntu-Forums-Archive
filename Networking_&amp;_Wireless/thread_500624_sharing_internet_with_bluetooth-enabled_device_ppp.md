---
title: "sharing internet with bluetooth-enabled device: ppp edition, help with routing/masq"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by A-1337 on 2007-07-14
Hello!
I have ubutnu workstation connected to internet via PPP-link (ppp0 interface in routing table). I want to share internet with bluetooth-enabled PDA.
I've configured PAN connection between workstation and PDA so they are in network 10.0.0.0 (bnep0 interface in routing table). They have static ip-addresses both and I can ping workstation from PDA.

I don't know what to do to share internet connection with PDA (I've heard there are options: configure masquerading or configure routing). Please guide what to do. 

I've tried masquerading sample from palm-howto ([https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)) (as root):
```

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i ppp0 -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

```

Also tried setup routing (also as root):
```

route add <bnep0 network address> gw <workstation ip-address in ppp0 network>
route add <ppp0 network address> gw <workstation ip-address in bnep0 network>

```

Nothing helped.

My routing table:
```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.148.4.126   *               255.255.255.255 UH    0      0        0 eth0
192.168.144.254 *               255.255.255.255 UH    0      0        0 ppp0
10.21.0.0       *               255.255.252.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 bnep0
default         *               0.0.0.0         U     0      0        0 ppp0

```

My network interfaces:
```

bnep0     Link encap:Ethernet  HWaddr 00:E0:98:D1:A7:E0  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
...
eth0      Link encap:Ethernet  HWaddr 00:80:48:22:B2:21  
          inet addr:10.21.1.31  Bcast:10.21.3.255  Mask:255.255.252.0
...
lo        Link encap:Local Loopback  
...
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.144.161  P-t-P:192.168.144.254  Mask:255.255.255.255
...

```

---

### Post by ederic on 2008-06-22
Something like this would be very helpful for me as my Palm isn't wifi-enabled.

---

