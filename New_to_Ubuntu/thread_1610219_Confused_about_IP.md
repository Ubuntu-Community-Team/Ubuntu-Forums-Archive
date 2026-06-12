---
title: "Confused about IP"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by Hazel99 on 2010-10-31
Hi, this is just a quick question to do with IP addresses and communicating between computers on different networks. I'm sure it's something very simple, but it's something that has got me kinda confused.
Anyway, if my computer was to communicate across the internet to a computer upon a different network, how would I specify which machine on that network I wanted to communicate with. For example, I might know it's internal IP address (192.168.etc.etc), but I can't use that; I need to use the public IP address, which obviously I also know. The problem is, though, that the public IP address will be the same for all the computers on that network, so how do I specify?
For instance, this may not be the best example, but... say I was trying to telnet to one of these machines, how could I specify which one? Would I just use the public IP address and the port number that is open on the machine I want to access? What if two machines on the internal network have this same port open (is that possible?)- how would I differentiate?
Like I said, I'm sure it's something quite simple, but it has me stumped, and I can't find out anywhere. I've searched a lot, and have been reading up on tcp/ip, but I stil can't figure it out.
I'm quite new to all this, so, if anyone can give some help, it would be greatly appreciated - including, if anyone has any, links to good sources of information I can read up on, from.

Hazel

---

### Post by peculiar penguin on 2010-10-31
> The problem is, though, that the public IP address will be the same for all the computers on that network, so how do I specify?You can't. Multiple computers will be behind some sort of router doing [NAT]("http://en.wikipedia.org/wiki/Network_address_translation"), and since your connection wasn't initiated by one of the internal computers, it'll go nowhere - the router simply doesn't know where your packets are supposed to go.

For this to work the remote network admin has to set up [port forwarding]("http://en.wikipedia.org/wiki/Port_forwarding") on the router, and you'll have to use that specific port.

---

### Post by The Cog on 2010-10-31
peculiar penguin has it right. I brief, you configure the router with a set of rules that say that incoming connections for **this** port should be forwarder to **that** computer etc. So essentially, one computer address provides one service. For example, incoming connections to port 80 (web service) at my house are forwarded to 192.168.2.56, my web server.

It is also possible on most routers to specify one address that **everything** gets forwarded to, which can be easier sometimes.

---

### Post by adit on 2010-10-31
My school has 30 computers.  All 30 computers have the same IP number (external IP number).  Suppose I send a webpage request from computer No.5.  How does the server (in external network) send the webpage exactly to the computer No.5?  Does it send any port numbers along with the IP numbers in every packet?

---

### Post by JKyleOKC on 2010-10-31
Your school's router maintains a table that associates computer number 5 with packets sent to a specific Ip address and port; replies to those packets then cause the router to look into the table, find which computer requested them, and forward them to that machine. This is, in broad terms, how Network Address Translation (NAT) works.

For NAT to operate, the connection has to be initiated locally. For attempts to connect from outside, port forwarding has to be set up.

---

### Post by The Cog on 2010-10-31
> **adit said:**
> My school has 30 computers.  All 30 computers have the same IP number (external IP number).  Suppose I send a webpage request from computer No.5.  How does the server (in external network) send the webpage exactly to the computer No.5?  Does it send any port numbers along with the IP numbers in every packet?
Yes. 
And if two computers choose to call from the same port number, the router will translate/substitute a different port number to keep them distinct. The router keeps careful track of all the translations is is currently performing.

---

