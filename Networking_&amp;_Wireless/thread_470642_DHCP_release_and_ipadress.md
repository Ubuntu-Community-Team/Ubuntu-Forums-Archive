---
title: "DHCP release and ipadress"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by mmorph on 2007-06-11
Hello, 
I am trying to connect to a network that uses automatic DHCP, they all start with 172.....

I guess I get no correct ippadress, but the question is why and what can I do about it?! The network uses LAN-guard but the MAC-adress of the computer is registrered there, and it is visible as well (ie the router sees it).

the result of:
sudo dhclient

...
Listening on LPF/eth0/00:13:d4:ec:bc:2f
Sending on LPF/eth0/00:13:d4:ec:bc:2f
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.16.229.253
bound to 192.168.0.106 -- renewal in 344396 seconds.

An extract of:
lspci

0000:00:12.0 Ethernet controller: VIA technologies, Inc. VT6102 [Rhine-II] (rev 78)

---

### Post by EndPerform on 2007-06-11
It seems to be giving you an address just fine.  I would think if the MAC address weren't registered at all, it would not give you anything.  It may be that the router is set up to give out addresses in that range.  Have you gotten a 172 address from this router before?  Also, is the network working?  Can you get to the internet or other machines?

---

### Post by mmorph on 2007-06-11
The network is NOT giving me an adress as far as I can tell. 

ifconfig:

inet addr: 192.168.0.106 

That is an ip that is not given from the network but probably something that is given as a standard when it gets no ip?

Yes, the network is working fine. Runs like a kitten on Windows machines...

---

### Post by EndPerform on 2007-06-11
```

Listening on LPF/eth0/00:13:d4:ec:bc:2f
Sending on LPF/eth0/00:13:d4:ec:bc:2f
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.16.229.253
**bound to 192.168.0.106 -- renewal in 344396 seconds.**

```

The line I have highlighted is what dhclient received from the router, so it is indeed getting an address from your router.  If it were to default to something, it would most likely start with 169.  And what I meant by your network was on the machine you're trying to get up and running.  Try getting somewhere on the net with that machine and let me know.

---

### Post by mmorph on 2007-06-11
Ok, so, if I understand you correctly you mean that the network hands out that adress (192.168.0.106) even though it should hand out 172.something?

In that case there supposedly could be something blocking access on account of it being a bad ip as far as the network is concerned? 

Lets for instance say that the router hands out the 192-adress, but the gateway only lets 172-adresses pass?

I can of course do a dual boot on the machine, but i rather not, so if my reasoning above is correct, please tell me so I can check the gateway instead... Thanks lots!!!:KS

---

### Post by mmorph on 2007-06-11
Yes, that was it. After the ip-range had been fixed everything worked fine. Thanks a lot for all the help though! :D

---

