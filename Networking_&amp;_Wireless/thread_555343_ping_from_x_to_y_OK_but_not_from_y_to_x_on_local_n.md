---
title: "ping from x to y OK but not from y to x on local network"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by dannemil on 2007-09-20
I had set up a server using ubuntu. It is connected to a router. It was working just fine. My wife could access the server from her windoze machine, and I could access it from my Ubuntu Feisty machine. All three machines were on the same subnet.

Then I had to reconfigure the network for various reasons (I know - that was my first mistake). In doing this, I moved my wife's machine and the Ubuntu server to a different subnet. Now I can no longer access the server shares (I changed the ip address appropriately in my fstab after the reconfiguration but it won't mount). The odd thing is that I can ping the server from my machine and it is successful, but not vice versa - the server cannot see or ping my machine.

I suspect this is some kind of routing issue that is beyond my abilities, so perhaps someone with a similar configuration could lend a hand.

It now looks something like this:

internet
|
|
[cable modem]
|
|
[Router (192.168.15.1)] ---- [Ubuntu server 192.168.15.103]
|
|                                             
[Wireless Router (192.168.15.101; locally 192.168.1.1]
|
|
[My machine DHCP 192.168.1.101]

(The reason for this is that the 192.168.15.1 router is a Vonage VoIP router without wireless, so I needed the other router to give me a way for my machine to connect.)

So the fact that the Ubuntu server cannot see or ping my machine (192.168.15.103  --//--> 192.168.1.101), but my machine can ping the server (192.168.1.101 ---> 192.168.15.103) says what???

Also the fact that I can ping the server, but I can no longer access the share through samba (which I could before I reconfigured the network) says what???

Any help much appreciated.

Jim

---

### Post by Jussi Kukkonen on 2007-09-20
I'm guessing  the wireless router creates another network for it's clients and they won't be available from the outside (outside being the VOIP router). Check wireless router settings: you can probably open the firewall and forward all traffic to your machine. Remember to make the IP somehow constant...

---

### Post by Ashlord on 2007-09-20
internet
|
|
[cable modem]
|
|
[Router (192.168.15.1)] ---- [Ubuntu server 192.168.15.103]
|
|
[Wireless Router (192.168.15.101; locally 192.168.1.1]
|
|
[My machine DHCP 192.168.1.101]



The reason you are able to ping the ubuntu server and not vice versa is because of this:
1. Packet goes from 1.101 to 1.1 and say "bring me to 15.103. I don't care wtf you do.. just bring me there. You are my default route."
2. Wireless router, simply sends the data to router (15.1).
3. Router knows ubuntu server is on its internal interface, so it sends the packet there.
4. And back. 15.103 -> 15.1 -> 15.101 -> 1.1 -> 1.101.

When you try to ping from the ubuntu box, the packet goes to router.
But router doesn't know where 1.x is.... so it sends to your ISP and your ISP tells you to go away.

:)

Solution to that is to add a static route on your router to forward 192.168.1.0/24 to 192.168.15.101

---

### Post by dannemil on 2007-09-20
> **Ashlord said:**
> internet
|
|
[cable modem]
|
|
[Router (192.168.15.1)] ---- [Ubuntu server 192.168.15.103]
|
|
[Wireless Router (192.168.15.101; locally 192.168.1.1]
|
|
[My machine DHCP 192.168.1.101]



The reason you are able to ping the ubuntu server and not vice versa is because of this:
1. Packet goes from 1.101 to 1.1 and say "bring me to 15.103. I don't care wtf you do.. just bring me there. You are my default route."
2. Wireless router, simply sends the data to router (15.1).
3. Router knows ubuntu server is on its internal interface, so it sends the packet there.
4. And back. 15.103 -> 15.1 -> 15.101 -> 1.1 -> 1.101.

When you try to ping from the ubuntu box, the packet goes to router.
But router doesn't know where 1.x is.... so it sends to your ISP and your ISP tells you to go away.

:)

Solution to that is to add a static route on your router to forward 192.168.1.0/24 to 192.168.15.101


OK so I tried to do this on my router (192.168.15.1) and got this in the routing table:

Destination LAN IP	Subnet Mask	Default Gateway	Hop Count	Interface
192.168.1.0	255.255.255.0	192.168.15.101	1	LAN

But still no luck. Still can't ping from the server to my machine. The VoIP router is so primitive that it won't let me add a range of IP's (I assume that was what the 192.168.1.0/24 meant).

I tried adding the specific machine IP 192.168.1.101 as a route, but it changed it in the routers routing table to 192.168.1.0.

What am I doing wrong?

---

### Post by Ashlord on 2007-09-20
Destination LAN IP Subnet Mask Default Gateway Hop Count Interface
192.168.1.0 255.255.255.0 192.168.15.101 1 LAN

This looks correct to me. Does your wireless router have any kind of spi firewall?

---

### Post by dannemil on 2007-09-20
> **Ashlord said:**
> Destination LAN IP Subnet Mask Default Gateway Hop Count Interface
192.168.1.0 255.255.255.0 192.168.15.101 1 LAN

This looks correct to me. Does your wireless router have any kind of spi firewall?

Thanks. How do I tell if it has an spi firewall, and if it does how do I modify it to allow those packets to pass on to the correct computer?

---

### Post by Ashlord on 2007-09-20
Just disable any firewall you have on your wireless router. Typical routers like WRT54G have internal firewall rules that work like 
INPUT : -m state --state ESTABLISHED,RELATED
OUTPUT: -m state --state NEW,ESTABLISHED
on the wan interface.

From 15.1, try to ping 15.101 and see if you get anything.

Then try pinging 1.1 and 1.101.

---

### Post by dannemil on 2007-09-20
> **Ashlord said:**
> Just disable any firewall you have on your wireless router. Typical routers like WRT54G have internal firewall rules that work like 
INPUT : -m state --state ESTABLISHED,RELATED
OUTPUT: -m state --state NEW,ESTABLISHED
on the wan interface.

From 15.1, try to ping 15.101 and see if you get anything.

Then try pinging 1.1 and 1.101.

Hey, something we did worked! I think it was setting that static route that allowed the 15.1 router to direct traffic meant for 1.101 through 15.101 (1.1).

I am now a happy camper as I can once again use my ubuntu server. Thanks.

---

### Post by lonce on 2007-09-20
Most routers will not let you connect inside the router.  Meaning if you ran a website on a server in your house.  If you typed the address from your pc, you would not see your website.  It gives you a 404.  If you went to google, searched for it, then went to it, it would work because its coming from an outside IP.

Dont know why they do it, but I have run into this many times running servers from home.  No way around it other than another router.

---

