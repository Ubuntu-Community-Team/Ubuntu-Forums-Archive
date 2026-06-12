---
title: "Share Internet Connection"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by idipous on 2007-05-09
I have two pc running ubuntu and fedora core 6. The ubuntu box has to NIC eth0 and rausb1.

rausb1 is a usb wirelless card I use to connect to the internet. The eth0 is used to connect to my other pc running fedora core. 

rausb1 has an ip adress 192.168.1.xx and eth0 has 192.168.0.13. 

What I want to do is to share the internet connection between the two boxes. At the fedora core I have eth0 with ip 192.168.0.2. 

I ran the following commands 

echo "1" > /proc/sys/net/ipv4/ip_forward
 iptables -t nat -A POSTROUTING -s 192.168.0.2 -o rausb1 -j MASQUERADE
iptables -I FORWARD -j ACCEPT -s 192.168.0.2

but the fedora box does not see the internet. What am I doing wrong?

thanks in advace
Adnreas

---

### Post by spd106 on 2007-05-10
Have you set the default gateway and DNS server on the Fedora box?

---

### Post by idipous on 2007-05-11
Yes done that and now works. Thanks...

idipous

---

