---
title: "ubuntu as router, cable"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by xolot1 on 2007-09-14
im trying to set up my webserver/ftp/ssh/yaddayadda server to be my router (my last one stopped working).  ive been trying to use webmin just cause it was the first thing i came to, and i have next to no understanding regarding iptables. in any case, im having trouble getting two computers who are drectly connected to each other to communicate.

i recall my father mentioning (as we made custom length cat5 cables) that when two computers are directly connected to each other, you need to switch the order of the cat5 wires (aka use a different cable). is this actually the case/should i be using a different cable then one i might use to plug into a hardware router?  or is it just my poor configuration that is holding me back?

thanks!

---

### Post by rivalarrival on 2007-09-14
You probably do need a crossover cable if you are going from computer-to-computer with an ethernet cable.

Usually there are two little lights under/beside the ethernet port - do they light up when both comptuers are hooked up? 

Check each ethernet port (and the cables) by using the modem, a switch, a hub, a router or whatever on the other end. If they light up with a network toy on the other end but not another computer, you need a crossover cable or a network toy between the connection. 

A cat 5 cable has 8 wires in 4 twisted pairs. It only uses 4 wires (2 pairs) for traffic - one pair transmits and the other pair receives. Ethernet toys are generally wired opposite NIC cards - the transmit of the nic card are in the same position as the receive on the ethernet toy, so you use a "straight" cable. 

But, connecting two NIC cards with a straight cable points the transmit pins of one nic card to the transmit pins of the other nic card - same thing with the receive pins.


As far as webmin - I got pretty good results by using the Shorewall webmin module to do my NAT routing and internet gateway functions. I also setup dnsmasq so my server would handle the dns translation.

---

