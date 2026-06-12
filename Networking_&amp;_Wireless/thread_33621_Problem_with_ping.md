---
title: "Problem with ping"
date: 2005-05-11
forum: Networking &amp; Wireless
---

### Post by Snower on 2005-05-11
Hello I have a problem with reaching computers in my network. When I use my wireless on my laptop I can ping the router an surf on the internet but I can't reach other conputers on my network. When I connect a cable on my network and us eth0 I can reach the other computer . can somebody help me with this proble?

---

### Post by lt_kije on 2005-05-11
[QUOTE=Snower]Hello I have a problem with reaching computers in my network. When I use my wireless on my laptop I can ping the router an surf on the internet but I can't reach other conputers on my network. When I connect a cable on my network and us eth0 I can reach the other computer . can somebody help me with this proble?[/QUOTE]
 Can you give us more information about your network? Could it be that the wireless network is on a differnet subnet or otherwise segregated from your wired net?

---

### Post by Snower on 2005-05-11
this is my wireless configuration the IP is recieved by dhcp by the router (192.168.3.1), I can ping the router but the computer that is connected to the router by cable (192.168.3.100 win xp) not?

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:35:B3:A3  
          inet addr:192.168.3.101  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe35:b3a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2562 errors:3 dropped:3 overruns:0 carrier:0
          collisions:505 txqueuelen:1000 
          RX bytes:821263 (802.0 KiB)  TX bytes:277243 (270.7 KiB)
          Interrupt:11 Base address:0x4000

---

### Post by lt_kije on 2005-05-11
Is your Windows XP box configured to respond to ICMP packets? Check the firewall there. Can you ping eg google.com?

---

### Post by Snower on 2005-05-11
yes I can ping [www.google.be](www.google.be), and I think that the firewall settings are good cause when I'm using a cable instead of the wireless everything is OK. I find it very strange and I can't find a solution. I thing there is a problem with ARP but I don't know what to configure.

---

### Post by lt_kije on 2005-05-11
Can your Windows XP box ping your Ubuntu box when it's connected via wireless?

---

### Post by Snower on 2005-05-11
No, the Xp box can't ping the ubuntu system either when it is connected to the wireless.

---

### Post by lt_kije on 2005-05-11
Weird. What model router do you have? Do you have any firewall rules running on your Ubuntu box?

---

### Post by grakhul on 2005-05-12
What are your IP addresses?  For the Ubuntu Box for the Windows Box and the router?

---

### Post by Snower on 2005-05-13
Ubuntu box: 192.168.3.101
Windows box: 192.168.3.100
Router (canyon): 192.168.3.1

all recieved by dhcp

---

### Post by grakhul on 2005-05-15
1.  Make sure that they are on the same subnet.
2.  Make sure that you have "enabled" windows networking on your Ubunut box.  This can be found in the network connection settings(System configuration -> Networking.
3.  Make sure that your Windows box and your Ubuntu box are on the same lan.  Some routers allow you to specify different LAN's depending on your IP addressing scheme.

---

