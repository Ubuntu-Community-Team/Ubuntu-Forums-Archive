---
title: "Two comps under one static IP"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Bost on 2008-07-24
My ISP gave me just one single static IP address under which I'd like to connect multiply computers (ubuntu 8.04) to internet and to each other (see scheme)
```

  Comp_1 ---+
            |  
            |  +--------+
            +--|        |     
               | switch +----- single static IP address for inet connection
            +--|        |
            |  +--------+
            |
  Comp_2 ---+
```

So I have inet access from every machine if I use the static IP for each computer but I have no connection: Comp_1 <-> Comp_2, and vice versa I have access: Comp_1 <-> Comp_2 for different IPs but in this case I lose inet connection on one of my comps.

Do you know how to solve it? Thx a lot...

---

### Post by eldragon on 2008-07-24
the most simple solution is to buy a router. 

that way, the router gets the isp's static ip, and then you get a LAN between the two computers connecting to the router. they both will have a LAN ip which will be different.

if buying a router is not an option, then you could always connect with one Ethernet port the isp's mdoem/cable/etcetera. and with another ethernet port connect both computers to the switch. (you will need 2 ethernet ports on one of the computers)

you will have to modify some iptables to get the first computer to route traffic to the second (act as a router).

i wouldnt really bother, and just buy a cheap router instead.

---

