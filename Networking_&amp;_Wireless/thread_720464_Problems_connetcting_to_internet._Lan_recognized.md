---
title: "Problems connetcting to internet. Lan recognized"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by mariosoto on 2008-03-10
Hello. I'm newie. We are trying Ubuntu in a school, but we cannot connect Ubuntu to the Internet. The system recognizes the local network and transfers files, prints and everything. I have the same configuration that is been user in Windows (XP by the way). Static IP. The problem seems to be that the system doesnot recognizes the GateWay.

IP 172.17.1.18
Mask 255.255.255.0
GW 172.17.0.1
DNS1 200.49.160.31
DNS2 200.49.160.35

I've pinged to 172.17.0.1 but all packages are lost. What could I do to try. I've searched documentation and some threads in this and other forums but i've found no similarities.

Mario Soto
..._

---

### Post by lloyd_b on 2008-03-10
> **mariosoto said:**
> Hello. I'm newie. We are trying Ubuntu in a school, but we cannot connect Ubuntu to the Internet. The system recognizes the local network and transfers files, prints and everything. I have the same configuration that is been user in Windows (XP by the way). Static IP. The problem seems to be that the system doesnot recognizes the GateWay.

IP 172.17.1.18
Mask 255.255.255.0
GW 172.17.0.1
DNS1 200.49.160.31
DNS2 200.49.160.35

I've pinged to 172.17.0.1 but all packages are lost. What could I do to try. I've searched documentation and some threads in this and other forums but i've found no similarities.

Mario Soto
..._

You LAN is in the 172.17.1.x range, but the specified gateway is in the 172.17.0.x range. WIth a netmask of 255.255.255.0, your computer simply doesn't know how to reach the gateway...

Please double check the values for Gateway (should it be 172.17.1.1 ?) and netmask (maybe 255.255.254.0 ?).  

Lloyd B.

---

### Post by mariosoto on 2008-04-28
> **lloyd_b said:**
> You LAN is in the 172.17.1.x range, but the specified gateway is in the 172.17.0.x range. WIth a netmask of 255.255.255.0, your computer simply doesn't know how to reach the gateway...

Please double check the values for Gateway (should it be 172.17.1.1 ?) and netmask (maybe 255.255.254.0 ?).  

Lloyd B.


Thanks Lloyd. Is for a school and our first steps on Ubuntu. We have installed this configuration for this machine, the same but in Windows. I also tried about five minutes earlier than this message with OpenSuse and worked fine.

I've thinked of that and I asked the network manager to give me a gateway for lab (we have 4), but until he feels so to doing it I have the same problem.

I don't know if I told that I have Ubuntu 7.10.

---

