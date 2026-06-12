---
title: "Two networks, two NIC's, one computer... is this possible?"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by insineratehymn on 2008-06-15
Ok, if that got you curious, I'll give you some topology:

Demarcation is a Siemens wireless DSL modem, due to restrictions on where the modem can be and where I can run cable (which happens to be nowhere) I must have this out of cable range of my server.

I am fine with the server not seeing the DSL modem, I would rather it not have a clear line to the internet anyway.

I have 3 nodes on a separate network which contains the server. 

In the middle ( or at least I want it to be ), is a laptop. I have it talking to the DSL modem via wireless USB. The router for the other network is within cable range of the laptop ( if I want to use it ). 

The laptop also has an on board ethernet port.

Now the question:
Can I have the laptop on the wireless network and the wired network at the same time? Do they have to be subnets on the same network? Can they be two entirely different networks?

I have no idea on how to approach this project.

My /etc/network/interfaces is default. I have not introduced any third party software into the mix.

I'm not looking primarily for an answer, but for ideas from people that are networking-ly gifted.

---

### Post by SpaceTeddy on 2008-06-15
first off, yes you can have a computer attached to as many subnets as you like. you can even have multiple subnets on the same network card if that makes you happy, or have multiple network card to act on the same subnet. All is possible. 

Now, back to the point:
What you want to do is only possible with a manual configuration of your network card, as network manager does NOT support connections to two networks at the same time. I don't have the time to spell this out at the moment, but this [[COLOR="Blue"]article[/COLOR]]("http://ubuntuforums.org/showthread.php?t=684495") should get you started on NOT using network manager (at least for one of the connections).

The only other thing you should worry about for now it that the network cards MUST NOT, NEVER EVER be in the same subnet. Also, only one network card should have a default gateway set. Keeping that in mind, the rest does really not matter. 

hope it helps :)

---

