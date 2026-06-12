---
title: "Confused with IP addresses?"
date: 2015-04-03
forum: Networking &amp; Wireless
---

### Post by sponge2 on 2015-04-03
Hi there,

I struggled for a while to connect via ssh to my home computer (OsX) from my work computer (Ubuntu). I tried and tried and tried with "ssh username@IP_address" and got multiple error messages.

I thought the way to determine the destination IP address (the OsX machine) was to simply issue the command "ifconfig | grep inet" and enter it in the "ssh username@IP_address" expression mentioned above.

After visiting several forums I ran into [http://canyouseeme.org/](http://canyouseeme.org/) and saw a completely unfamiliar IP address that when entered in "ssh username@IP_address" made it work.

Why doesnt ifconfig display this IP address found with [http://canyouseeme.org/](http://canyouseeme.org/) ?

---

### Post by Doug S on 2015-04-03
Hi and welcome to Ubuntu forums.

Typically, the IP address of your computer is a LAN (Local area network) IP address, and not the WAN (Wide area network) IP address. When you go to places like canyouseeme, it will see your external or WAN IP address. The address translation between your LAN and the WAN is done by your router. ifconfig will only show the LAN address of your computer.

What I don't understand about your case, and would need more information to comment further, is if you were successful is ssh'ing from your office, then you would have to have port forwarding setup in your router, which means you would have to have known about this stuff to do it. And if, you do not have a router and your computer is connected directly to the WAN, then ifconfig should have shown the correct IP address and it should have been the same as what ifconfig showed.

---

### Post by sponge2 on 2015-04-04
Hi Doug and thank you for your reply.

My phone (android) is connected to the same LAN and canyouseeme.org is giving it the same IP address. Still confused, does this mean that if I had a second computer (lets say computer B) within the same LAN it would have the same WAN IP Address? If that is the case, if I ssh say from outside the LAN using the WAN IP address (the WAN IP address seems to be the only one that allows me to ssh from outside), which computer would I access? A or B?

---

### Post by SeijiSensei on 2015-04-04
Canyouseeme only reports the publicly-facing address on your router.  

For inbound SSH, what matters is which computer the router is configured to forward packets to.  If you open, say, port 2222 and forward it to one computer's port 22, then you could connect to that computer by using SSH to port 2222 on the external address.  If you open and forward port 2223 to the other computer's port 22, you could choose to connect to that computer over SSH as well using port 2223.

---

### Post by sponge2 on 2015-04-04
@Doug: I hope this helps answering the second part of your reply, when I tried ssh'ing my home Mac I first opened port 22 in my gateway (provided by the ISP).  But like I said, it's only when I use the WAN IP address and not the LAN one that I get ssh to work.

@SeijiSensei: Okay, so if I understand correctly, ssh requires two ports, one from the computer from which the data is sent and another port for the computer that receives the data. Is this correct? Can these ports be given any random number?

-- Thanks

---

### Post by Doug S on 2015-04-04
> **sponge2 said:**
> But like I said, it's only when I use the WAN IP address and not the LAN one that I get ssh to work.The LAN IP address would be from the reserved for private networks pool, and it would not be possible to route to it from the WAN. [See also]("http://en.wikipedia.org/wiki/Private_network"). > **sponge2 said:**
> @SeijiSensei: Okay, so if I understand correctly, ssh requires two ports, one from the computer from which the data is sent and another port for the computer that receives the data. Is this correct? Can these ports be given any random number?No, SSH requires only 1 port. The port used by the sending computer will be whatever high numbered port it decides to use. The point Seiji was trying to make was that you need two different destination ports if you want to be able to ssh to two different computers on your LAN, so that your router can direct the packets properly. In Seiji's example, your router would know that a packet destination port of 2222 should be forwarded to computer 1 and a packet destination of port 2223 should be forwarded to computer 2.

---

### Post by sponge2 on 2015-04-06
Thanks a lot for the help

---

