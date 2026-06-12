---
title: "i can connect vpn but nothing happen"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by nemanaldin on 2007-09-17
hi i can connect vpn by kvpnc on ubuntu feisty
but when i browse internet via firefox my ip not been changed 
i use vpn on ppp0 not network 
anyone can help 
thanks and sorry for my bad english

---

### Post by noob12 on 2007-09-17
You should check your default route.  If it is routing over the non-vpn interface, that may be the problem.

This will display your routing table:
```

route -n

```

---

### Post by nemanaldin on 2007-09-17
thanks for ur attention 
this is answer of command:
nemanaldin@nemanaldin:~$ route -n
Kernel IP routing table
Destination            Gateway                  Genmask                               Flags        Metric            Ref              Use Iface
192.168.1.1            0.0.0.0                   255.255.255.255 UH                0               0                  0               ppp1
10.10.10.10            0.0.0.0                    255.255.255.255 UH               0                0                 0                ppp0
169.254.0.0             0.0.0.0                   255.255.0.0     U                      0               0                  0               eth0
0.0.0.0                    0.0.0.0                    0.0.0.0         U                         0                 0                 0                ppp0

and this :
nemanaldin@nemanaldin:~$ sudo route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     *               255.255.255.255 UH    0      0        0 ppp1
10.10.10.10     *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

what can i do?
thanks again

---

### Post by noob12 on 2007-09-17
Do you know what the right gateway router is on ppp0?  Is it something other than 10.10.10.10 ?

---

### Post by nemanaldin on 2007-09-17
when i connected with kvpnc 
answer of route command this:
nemanaldin@nemanaldin:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     *               255.255.255.255 UH    0      0        0 ppp1
10.10.10.10     *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
default         *               0.0.0.0         U     1000   0        0 eth0

---

### Post by nemanaldin on 2007-09-17
sorry whats ur mean?
i connect to internet with modem by kppp
and when i click details have two address :
local addr: 80.191.251.28
remote addr: 10.10.10.10
and i want connect to vpn by kvpnc and have this problem 
how i can set my vpn connection defualt system connection to internet i think my problem this
thanks for ur answers

---

### Post by noob12 on 2007-09-17
OK.  So your basic ppp connection works, but kvpnc tries to establish a connection on eth0 instead, is that the problem?

---

### Post by nemanaldin on 2007-09-17
no my kvpnc connect as ppp1 
this is before i connected to vpn
nemanaldin@nemanaldin:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.10     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

---

### Post by nemanaldin on 2007-09-17
can we talk in yahoo messenger

---

### Post by noob12 on 2007-09-17
Not from my current location.  But later this evening PST.  I don't think I understand your problem.  I'm sorry but I am having trouble interpreting.

---

