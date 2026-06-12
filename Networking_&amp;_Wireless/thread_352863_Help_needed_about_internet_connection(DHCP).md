---
title: "Help needed about internet connection(DHCP)"
date: 2007-02-03
forum: Networking &amp; Wireless
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

### Post by gradedcheese on 2007-02-04
My solution for these troublesome PPPOE connections has always been to just plug in a cheap router between the modem and the computer(s).  The router will deal with PPPOE, giving you a normal DHCP address.  I know that's probably not the solution you're looking for but, I still think it's the way to solve it ;)  Basically, write down the settings (which you have done), go to the store and buy any home networking type router, plug the modem's ethernet cable into the router's WAN port, and your PC into one of the LAN ports and then just follow the manufacturer's instructions.  And then never deal with logging in or other PPPOE stuff again...

---

### Post by ukripper on 2007-02-05
If you don't want router then try follwoing link:

[http://www.ubuntuforums.org/showthread.php?t=44763&highlight=adsl+modem](http://www.ubuntuforums.org/showthread.php?t=44763&highlight=adsl+modem)
:KS

---

