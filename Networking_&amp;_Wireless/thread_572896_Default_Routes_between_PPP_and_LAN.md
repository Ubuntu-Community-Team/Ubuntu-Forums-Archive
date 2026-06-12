---
title: "Default Routes between PPP and LAN"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by darkwave80 on 2007-10-10
I have a lan which runs apache to the network and when I dail out on my PPP connection it is not making the PPP the default route to the internet , here is what it looks like when i do a netstat -rn

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
22.174.42.13    *               255.255.255.255 UH    0              0        0 ppp0
192.168.1.0     *               255.255.255.0        U     0            0        0 eth0
link-local           *                 255.255.0.0          U     1000   0        0 eth0
default         **192.168.1.1**     0.0.0.0              **UG**    0      0        0 **eth0**
default         *               0.0.0.0         U     0      0        0 ppp0


 where it says UG on eth0 , that is why it is looking at my local area network for websites.



     what do i have to do , to make the bottom "default"  change from U to UG to be the default route?

Seems like this is harder than it should be??

---

### Post by eendoe on 2007-10-11
route del default gw *
route add default gw 192.168.1.1?

---

