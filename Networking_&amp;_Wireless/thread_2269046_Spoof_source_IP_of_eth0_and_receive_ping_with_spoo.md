---
title: "Spoof source IP of eth0 and receive ping with spoofed address"
date: 2015-03-13
forum: Networking &amp; Wireless
---

### Post by Eu_Vern_Lee on 2015-03-13
Hi guys, newbie here.

This is the current setup of my network.
I'm using three PCs. One of them, PC A,  is running Ubuntu and has three NICs; eth0, wlan0, wlan1. The other PCs, PC B and C are running windows 7 and 8.1.

**Ubuntu Pc**
eth0 IP - 192.168.20.1
wlan1 IP - 192.168.10.1
wlan0 IP (Connected to router with internet): 192.168.0.10

**Others**
PC B is connected to eth0:
PC B Ip -192.168.20.2
PC C is connected to wlan1:
PC C IP - 192.168.10.2
[B]
IPTABLES for UBUNTU
[/B]
-A POSTROUTING -o wlan0 -j MASQUERADE
-A POSTROUTING -o wlan1 -j MASQUERADE
-A POSTROUTING -o eth0 -j MASQUERADE
-A POSTROUTING -o eth0 -j SNAT --to-source 1.2.3.4 (My attempt to spoof the IPs)
-A POSTROUTING -o wlan1 -j SNAT --to-source 1.2.3.4

-A FORWARD -i eth0 -j ACCEPT
-A FORWARD -i wlan1 -j ACCEPT

(I'm sure I'm using iptables wrongly)

Right now, I'm able to ping all the computers from each other without a problem. Also, PC B and C has internet connection which is also good.

However, what I'm trying to do now is to ping PC B from PC C(and vice versa) and have the receiving PCs show that the incoming ICMP packets are coming from the spoofed address. I will sniff the ICMP packets using wireshark.  

Here is the report that I'm currently getting from Wireshark when pinging from 192.168.10.2 to 192.168.20.2
24142    2448.636234000    192.168.20.1    192.168.20.2    ICMP    74    Echo (ping) request  id=0x0001, seq=63/16128, ttl=127 (reply in 24143)

It shows that the incoming packet is from the address of the interface that it connected to. Is there something I should change in my IPTABLES to have it work the way I want it to?

---

### Post by Hulk_Joshua on 2015-03-13
i dont think what you are trying to do is possible

---

### Post by Eu_Vern_Lee on 2015-03-13
well, I'm trying to do something similar to what this guy did.
[https://sandilands.info/sgordon/address-spoofing-with-iptables-in-linux](https://sandilands.info/sgordon/address-spoofing-with-iptables-in-linux)

---

