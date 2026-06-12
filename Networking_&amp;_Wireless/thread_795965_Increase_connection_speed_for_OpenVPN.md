---
title: "Increase connection speed for OpenVPN"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by kalyptus on 2008-05-16
Just installed Openvpn in Ubuntu... and aint got no problem connecting to it our client machines using both windows and ubuntu... However the icon in our Windows client displays that the connection speed of the tap connection is just 10 mbps... Is there a way to increase the connection speed? What should I do?

---

### Post by RumorsOfWar on 2008-05-17
I don't know, but if you asked on general help, you'd probably find someone who knows. Or I'm sure a moderator could move this there if you'd like. 
Good luck :)

---

### Post by p_quarles on 2008-05-17
Moved to Networking and Wireless.

---

### Post by kalyptus on 2008-05-19
Thanks for moving this thread to its proper place... But it seems my post doesn't have a clear reply up to this time... Anyone?

---

### Post by SpaceTeddy on 2008-05-20
is this a windows or a linux problem ? which tap (why tap ?) device are you talking about ? the windows or the linux one ?

I am confused :confused:

---

### Post by kalyptus on 2008-05-20
I am using ubuntu os as my server.. ubuntu and windows xp as my client... thanks

---

### Post by SpaceTeddy on 2008-05-20
ok, i got some time for tests. Since i do not have a windows install at hand at the moment, i have to rely on ubuntu(hardy) as the client to debian(lenny) as the server. Checking the connection speed settings on the network interfaces, they also give me 10Mbit/sec. here is the full output of the server
```
ethtool tun0
Settings for tun0:
	Supported ports: [ ]
	Supported link modes:   
	Supports auto-negotiation: No
	Advertised link modes:  Not reported
	Advertised auto-negotiation: No
	**Speed: 10Mb/s**
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Current message level: 0xffffffa1 (-95)
	Link detected: yes

```
and here is the full output of the client:
```
 sudo ethtool tun0
Settings for tun0:
	Supported ports: [ ]
	Supported link modes:   
	Supports auto-negotiation: No
	Advertised link modes:  Not reported
	Advertised auto-negotiation: No
	**Speed: 10Mb/s**
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Current message level: 0xffffffa1 (-95)
	Link detected: yes

```

With these settings a transfer of more than one Megabyte/sec should not really be possible - however, i can easily max out my dsl line (1,6 Mbyte) via this VPN. So i am assuming that the device speed is just displayed wrong. I would think they can go as fast as the underlaying real network device. This is only a theory. It still has to be tested.

---

### Post by kalyptus on 2008-05-21
Thanks... Your explanation makes me realize one thing... We are using internet... Really... really thanks a lot...

---

### Post by freshmeat20 on 2012-08-17
Im also wondering how to increase speed. Same setup, ubuntu server with a windows client. What can I do to increase past 10mbs?

---

### Post by wildmanne39 on 2012-08-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

