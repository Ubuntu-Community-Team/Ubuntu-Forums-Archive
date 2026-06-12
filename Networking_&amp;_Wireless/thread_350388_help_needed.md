---
title: "help needed"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by sandeep_37 on 2007-01-31
i am new to ubuntu and i am get internet connection . Help is needed how t install dhcp for the first time 
i dont know amyhting in ubuntu.

---

### Post by K.Mandla on 2007-01-31
Hi and welcome. DHCP should be set up already if you installed Ubuntu. If you know the interface name of your network card, you can connect it and use this command in a terminal to ask the router for an address.

```
sudo dhclient eth0
```
Make sure you change *eth0* to the interface for your card.

What kind of computer are you using? Do you know what kind of network card you have?

---

### Post by sandeep_37 on 2007-02-03
i am new to ubunt and linux. My connection is DHCP is a protocol (pppoe). In windows i go to give my ID and password in [www.reliance.co.in](www.reliance.co.in) that i can acess the net. I need not set anything there . I have adsl modem and i also know ip address,subnet,gateway,DHCP,dns,wins values. so how i have to do that in ubuntu .

Ethernet ADSL modem site for that is [www.utstar.com](www.utstar.com) model is UT-300R2 ethernet adsl modem . I have to give user id and password in the [www.reliancebroadband.co.in](www.reliancebroadband.co.in) which will open itself without connecting to net . This is DHCP type

there are only five protoco in adsl modeml
1 ppp over ATM(pppoa)
2 ppp over ethernet(pppoe)
3 mac encapsulated routing(MER)
4 IP over ATM(IPOA)
5 Bridging

Now what you want me to do?

plz help me
VPI/VCI Service protocol

0/32 br_0_32 bridge
8/35 br_8_35 bridge
0/35 br_0_35 bridge
8/81 br_8_81 bridge
14/24 br_14_24 bridge
0/100 br_0_100 bridge
0/33 br_0_33 bridge
0/40 br_0_40 bridge

---

