---
title: "IPtables traffic management?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Tixer on 2008-05-18
Using iptables, how can I forward a range of ports to one specific interface. I have a server with three cards, and I need to make sure that traffic on say, ports 6800 - 6810, only goes through eth1.

---

### Post by SpaceTeddy on 2008-05-19
mhm, without further information this is kind of hard to answer. Do you mean incomming, outgoing or passthrough traffic ? where are the pakets comming from, where are they directed ? do you want to do regular port portfarding (DNAT), do you only want to ACCEPT the these pakets on one interface to the machine itself (INPUT) do you only want to let them pass through the machine on a specific network card (FORWARD).

so, without more knowledge, i cannot assemble the fill commands :)
however, if you want network card specific rules, you can alsways use the -i and -o flags in the commands, which specify a network device that has to match for the pakets to be accepted by a rule. Maybe that is all you wanted to know ?

i am confused :confused:

---

### Post by Tixer on 2008-05-19
Basically, my ISP has started throttling BT traffic. To circumvent it, I need a computer to dial a pppoe connection that's set up as multilink. Rather than setting every computer in my house up to do this, I figured that I'd install a webui for azureus, have all machines add their torrents through there, and everything would be smooth. This part is already taken care of.

Since two network cards are needed (the first to talk to other computers on the network, the second to dial a ppp0 connection), I need to make sure that /all/ traffic coming from azureus goes to ppp0. Since this consists of multiple ports, I need to know how to redirect an entire port range so all traffic (incoming, outgoing, all that crap) can only travel through ppp0.

---

### Post by SpaceTeddy on 2008-05-19
call me stupid, but i still don't get it. 

Does your setup look like this ?

Internet
 |
Ubuntu ---> Azureus 
 |
Switch ---> Computer, Computer, Computer 

I have still no idea what you are trying to do... i feel silly :confused:

---

### Post by Tixer on 2008-05-20
Basically, here's a nice ASCII diagram of my setup, in all its confusing glory. Disregard the X's, as they're just there for formatting.

Modem --- Switch --- Router A --- My Desktop, HTPC and Server
XXXXXXXXXXX |              
XXXXXXXXXXX |-Router B - Parent's Computer / AP Upstairs / My Server (over Wifi)
XXXXXXXXXXX |                              
XXXXXXXXXXX |- Brother's Computer
XXXXXXXXXXX |
XXXXXXXXXXX |- My Server

Basically, my server has three network cards. The first one is used to share info between my server, desktop, and htpc (eth0). Since my server is in the basement near all the wiring, getting a direct connection to the internet isn't an issue, whereas to do so on my desktop and still share on a network would require tons of effort (running a second ethernet cable around my room)

The second network card, eth1, goes straight to the switch, and it dials a PPPoE connection.

The third network card is a wifi card used to share data with my parent's computer. My lovely HP printer is a footrest, so I just print to theirs.

So basically, the first and third network cards are (ideally) only used for file sharing on their networks. Since the second is the only one that can download unthrottled, I want to make sure that all BitTorrent traffic goes through that interface.

---

