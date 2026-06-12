---
title: "internet connection sharing problem with pppoe"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by drytear on 2007-08-04
Here it is, i have a pppoe connection, 2 ethernet cards, eth0 my external interface and eth1 my internal interface. i got internet connection sharing working but i have 3 problems. 
1. from time to time my internet connection dies, i sudo pppoeconf again and again until it's up again. It's not my provider's fault, something is happening here.
2. when the other computer shuts down, ubuntu says i'm disconnected too. Why ? both my ethernet cards are set to dhcp. 
3. when i set up a static ip for eth1 from the network manager it disconnects me completely from the internet all though my external interface is eth0. why? 

I'm lost here .. anyone got a suggestion?

---

### Post by boteeka on 2007-08-19
I'm not able to help you yet, but I would be interested on how you managed to share your pppoe connection. Maybe we can figure out something.

I also am in that kind of situation. I get my internet connection through a pppoe connection, which I set up using pppoeconf. It is working well, no problems here. Currently I installed another network card to share my internet connection with another machine which runs Windows XP. The WIN machine is set up to use DHCP for its address.

So on my Ubuntu (7.04 Feisty) machine I have now two phisical networking devices (an on-board ethernet [eth0] card and another I recently installed [eth1]). The cable coming from my ISP is plugged in eth0, and the cable between my machine and the other is plugged in eth1.

After I set up the pppoe connection, another networking device appeared: ppp0. This is not a phisical device, pppoeconf created it.

This is all good at this point. Now I would like to begin sharing this pppoe connection. I read a whole bunch of forum threads, tutorials, howtos, etc. Some of them offer command-line solutions to the problem involving iptables (I don't have problem with this), others say I should install dnsmasq, ipmasq and firestarter and with firestarter I can set it up running a wizard. Guess what? It doesn't work. The firewall won't start. Others suggested that I use Firewall Builder which is a very nice and great tool for someone who understands all these networking expressions, but not me. I have some basic knowledge about it, but frankly not enough.

My understanding is this:[LIST]
[*]I have a working pppoe connection to the internet - FINE
[*]I have a working connection to the other machine with which I want to share my internet connection - FINE
[*]My machine with the internet connection should act as a gateway to the other machine, optionally running a DHCP server to allocate an address to the other machine - DON'T KNOW HOW TO DO THIS[/LIST]Please explain how you managed to share your connection. Your response would be greatly appreciated.

---

