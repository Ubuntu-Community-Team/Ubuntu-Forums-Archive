---
title: "Clarifying some networking concepts."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by BlakeM on 2009-01-25
Ok, big noobie questions here. Just need to confirm a few things I've read:

1. The purpose of a router connected to an internal network is to prevent harmful information sent from an external network reaching devices connected to the internal network.

2. A router has ports that are either open or closed. The ports that are open or closed on a router can be configured by the Network Administrator. If a port is open, packets of data that are sent from external networks can pass through the port. If a port is closed, packets of data cannot pass through.

3. If the packets of data are passed through an open port, the router then routes the packets to the appropriate internal IP address.

4. A software firewall, like iptables, adds an extra layer of security on top of a hardware firewall. It will filter all packets that the computer receives from the router and determine if they are safe/appropriate. You can configure iptables to filter packets according to a set of rules. These rules can make sure that, for example, only packets that have been correctly identified as SSH packets are allowed through.

5. On a default "virgin" installation of Ubuntu 8.04 iptables is not enabled by default. However, no services are installed by default, so no programs are listening on any ports. If no programs are listening to ports, then you don't need to worry about a firewall?

6. Most routers close all ports by default. So, if I want to use a service like SSH, I have to open a port on my router (22 by default) to allow packets from an external network to be sent to the appropriate internal IP address. The external network, if behind a router, must also have its router configured to allow SSH packets and have them routed to the appropriate internal IP address. (Software firewalls at both ends must also be configured to allow and filter traffic on the appropriate port).

7. If I install services like Apache, SSH and MySQL, I should configure iptables and my router to allow these packets to pass through the appropriate ports. If I open these ports on my router, I should configure iptables to filter these packets to make sure malicious packets don't get through. I should also configure iptables to only allow packets from trusted external IP addresses. I should also set very strong passwords for authenticating use of these services and use public keys for SSH.

Ok, I've got a few other questions but I'll stop myself here. I'm pretty sure I've got a basic understanding. If any of this is wrong please let me know. I've been reading a lot of stuff on the Security forums. Just need a few things clarified. Thanks for taking the time to read and answer my questions.

P.S. I accidentally posted this in the security forum. I don't think that's where I should have posted so I moved this thread to here. Wasn't sure if I could delete/move threads properly so I've created a duplicate thread. Could a moderator please clean up my mess? Thanks.

---

### Post by amauk on 2009-01-26
> **BlakeM said:**
> 1. The purpose of a router connected to an internal network is to prevent harmful information sent from an external network reaching devices connected to the internal network.The purpose of a router is to connect 2 or more networks together

A1 = machine 1 on network A
Ar = External router to network A
etc.

```
Network A           Network B

A1----              ----B1
     |              |
A2---+--Ar------Br--+---B2
     |              |
A3----              ----B3
```

Any information passing between network A & B needs to pass through the routers

As the name suggests, routers route traffic to the correct locations when communicating across networks

An added benefit, is that individual machines are separated from the outside world, and hence it's more secure. But this isn't the primary goal, just an added benefit

> **BlakeM said:**
> 2. A router has ports that are either open or closed. The ports that are open or closed on a router can be configured by the Network Administrator. If a port is open, packets of data that are sent from external networks can pass through the port. If a port is closed, packets of data cannot pass through.

3. If the packets of data are passed through an open port, the router then routes the packets to the appropriate internal IP address.Correct
the routers job is to route packets to the correct location
For example, router Br may route Port 22 to machine B2
If no route is specified for a port, the packet is dropped

> **BlakeM said:**
> 4. A software firewall, like iptables, adds an extra layer of security on top of a hardware firewall. It will filter all packets that the computer receives from the router and determine if they are safe/appropriate. You can configure iptables to filter packets according to a set of rules. These rules can make sure that, for example, only packets that have been correctly identified as SSH packets are allowed through.It's not an "extra" layer of security, as such
it's the same level of security
Linux uses IPtables to route incoming packets
that's all

> **BlakeM said:**
> 5. On a default "virgin" installation of Ubuntu 8.04 iptables is not enabled by default. However, no services are installed by default, so no programs are listening on any ports. If no programs are listening to ports, then you don't need to worry about a firewall?No,
IPtables is always enabled
You can't disable it (you'd lose all connectivity)
On a virgin install of Linux, by default, all ports are "closed" (Ie. there's no routing specified for the port)
When you install some software that listens on a port, the port is opened

> **BlakeM said:**
> 6. Most routers close all ports by default. So, if I want to use a service like SSH, I have to open a port on my router (22 by default) to allow packets from an external network to be sent to the appropriate internal IP address. The external network, if behind a router, must also have its router configured to allow SSH packets and have them routed to the appropriate internal IP address. (Software firewalls at both ends must also be configured to allow and filter traffic on the appropriate port).For most nwtworks, outgoing connections are not restricted
If A1 wants to SSH into B3, Br needs to route port 22 to B3
Under general usage, no config needs to be changed on Ar

> **BlakeM said:**
> 7. If I install services like Apache, SSH and MySQL, I should configure iptables and my router to allow these packets to pass through the appropriate ports. If I open these ports on my router, I should configure iptables to filter these packets to make sure malicious packets don't get through. I should also configure iptables to only allow packets from trusted external IP addresses. I should also set very strong passwords for authenticating use of these services and use public keys for SSH.If you install server software, by default the corresponding ports will be opened automatically
The purpose of software firewalls like Firestarter or UFW is to give you some selective control over when packets are accepted or not

Without a firewall, it's all or nothing - port is either closed to everybody or open to everybody
With a firewall, it's more configurable and you can write rules for certain IP addresses, packet contents, etc.

---

### Post by diablo75 on 2009-01-26
> **BlakeM said:**
> Ok, big noobie questions here. Just need to confirm a few things I've read:

1. The purpose of a router connected to an internal network is to prevent harmful information sent from an external network reaching devices connected to the internal network.



That's not it's sole purpose.  A router (as it functions between a LAN and the Internet) acts like a butler.  When inbound "mail" comes in from the Internet "Postal Service", he'll filter it to determine if inbound messages are legit, or probably junk mail.  He does this job mostly by keeping a little notebook of who in the house has sent messages out to the Internet, and where they were sent too (because he expect to see a reply come back from that recipient within a short period of time, so that when a reply comes back, he knows exactly who to pass it along to).  (Get's more complicated... so let me read what you're other questions are).
> 
2. A router has ports that are either open or closed. The ports that are open or closed on a router can be configured by the Network Administrator. If a port is open, packets of data that are sent from external networks can pass through the port. If a port is closed, packets of data cannot pass through.

Correct.  When someone in the house sends mail out, it's tagged with a "source port" and the butler (the router) jots that down for a few minutes.  The recipient sees this port number, so when it replies to the IP address guarded by the butler, the butler will see this port number and say, "Ah yes.  Mr. Jones in room 4 sent something to you; he's expecting a reply.  I will pass this along to him.  Thanks!  Bye!"

Sometimes residents in the house (the LAN) want to sent up perminant rules that the butler will obey, like port forwarding.  For instance, you will say, "Butler!  I want all inbound messages addressed to our house, for port number XXXXX to be forwarded to my room!"  "Yes sir!"
> 
3. If the packets of data are passed through an open port, the router then routes the packets to the appropriate internal IP address.

Only if it knows where to send it, either because a previous session of outbound communication was started and the butler knows about it, or because there's a port-forwarding rule he's been told to obey.
> 
4. A software firewall, like iptables, adds an extra layer of security on top of a hardware firewall. It will filter all packets that the computer receives from the router and determine if they are safe/appropriate. You can configure iptables to filter packets according to a set of rules. These rules can make sure that, for example, only packets that have been correctly identified as SSH packets are allowed through.

Yes.  It is an extra layer, but it filters on the same principle that the butler filters on:  port numbers.
> 
5. On a default "virgin" installation of Ubuntu 8.04 iptables is not enabled by default. However, no services are installed by default, so no programs are listening on any ports. If no programs are listening to ports, then you don't need to worry about a firewall?

Incorrect.  iptables is always on.  You're right about the rest of it.  iptables is the firewall.  Enabling services (like ssh-server or VNC for example) tells iptables to make exceptions and open up ports 22 or 5900 for said services.  Sometimes this has to be done manually.
> 
6. Most routers close all ports by default. So, if I want to use a service like SSH, I have to open a port on my router (22 by default) to allow packets from an external network to be sent to the appropriate internal IP address. The external network, if behind a router, must also have its router configured to allow SSH packets and have them routed to the appropriate internal IP address. (Software firewalls at both ends must also be configured to allow and filter traffic on the appropriate port).

The external network.... I'm not exactly sure what you mean by this.  If you're referring to the Internet, all it cares about is the IP address.  Are we talking about two routers between a PC and the Internet?  If so, then yes.  Port forwards would have to be set up at the end closest to the Internet.  Depending on the IP addressing scheme, you may not need to set up a port forward on the second router because it would seem to be doing little more in this scenario than to function as a switch (unless the IP address on the "inside"(facing the PC) are on a different network than the IP addresses on the "outside" (facing the outer router, and the Internet beyond that).

So...

Internet----Router------Router2------PC???

> 

7. If I install services like Apache, SSH and MySQL, I should configure iptables and my router to allow these packets to pass through the appropriate ports. If I open these ports on my router, I should configure iptables to filter these packets to make sure malicious packets don't get through. I should also configure iptables to only allow packets from trusted external IP addresses. I should also set very strong passwords for authenticating use of these services and use public keys for SSH.

You actually should expect malicious packets to get through if you are setting up a server.  An open port is an open port.  So using things like public-key authentication for services like SSH is a must if you want to be extra safe.  Passwords should also be very strong.

> 

Ok, I've got a few other questions but I'll stop myself here. I'm pretty sure I've got a basic understanding. If any of this is wrong please let me know. I've been reading a lot of stuff on the Security forums. Just need a few things clarified. Thanks for taking the time to read and answer my questions.

P.S. I accidentally posted this in the security forum. I don't think that's where I should have posted so I moved this thread to here. Wasn't sure if I could delete/move threads properly so I've created a duplicate thread. Could a moderator please clean up my mess? Thanks.

I think you got it down pretty well.  Good job!

---

### Post by jerome1232 on 2009-01-26
> **BlakeM said:**
> cOk, big noobie questions here. Just need to confirm a few things I've read:

1. The purpose of a router connected to an internal network is to prevent harmful information sent from an external network reaching devices connected to the internal network.

No not quite. A router is NAT (Network Address Translation), dhcp server and a firewall. NAT allows multiple computer to share one public ip address and get the internet without getting an additional public IP address. DHCP server allows your local computers to get a private ip address assigned to them by the router. For the firewall part see #2

> **BlakeM said:**
> 
2. A router has ports that are either open or closed. The ports that are open or closed on a router can be configured by the Network Administrator. If a port is open, packets of data that are sent from external networks can pass through the port. If a port is closed, packets of data cannot pass through.

Again close but not quite. A router drops all incoming traffic unless configured to forward traffic to specfic computer on specific ports. IE The router can be told that if any traffic is recieved on port 22, forward the connection to 192.168.1.15. 

> **BlakeM said:**
> 
3. If the packets of data are passed through an open port, the router then routes the packets to the appropriate internal IP address.

Yes if packets arrive on a port that is forwarded to another computer they get sent it's way.

> **BlakeM said:**
> 
4. A software firewall, like iptables, adds an extra layer of security on top of a hardware firewall. It will filter all packets that the computer receives from the router and determine if they are safe/appropriate. You can configure iptables to filter packets according to a set of rules. These rules can make sure that, for example, only packets that have been correctly identified as SSH packets are allowed through.

Yes, although I perfer hardware firewalls anyday (malware can't turn off my router)

> **BlakeM said:**
> 
5. On a default "virgin" installation of Ubuntu 8.04 iptables is not enabled by default. However, no services are installed by default, so no programs are listening on any ports. If no programs are listening to ports, then you don't need to worry about a firewall?

iptables is enabled by default it just allows all traffic, by default no ports are open to the internet on a default installation of Ubuntu so a firewall doesn't do a think to make the computer more secure. If you run a server there are various reasons you may want to start adding some rules to iptables.

> **BlakeM said:**
> 
6. Most routers close all ports by default. So, if I want to use a service like SSH, I have to open a port on my router (22 by default) to allow packets from an external network to be sent to the appropriate internal IP address. The external network, if behind a router, must also have its router configured to allow SSH packets and have them routed to the appropriate internal IP address. (Software firewalls at both ends must also be configured to allow and filter traffic on the appropriate port).

Actually only the server side needs to have the router configured to forward ports, routers will not stop outgoing traffic, only incoming. Some software firewalls to regulate outgoing traffic and you may have to configure them to allow traffic.

> **BlakeM said:**
> 
7. If I install services like Apache, SSH and MySQL, I should configure iptables and my router to allow these packets to pass through the appropriate ports. If I open these ports on my router, I should configure iptables to filter these packets to make sure malicious packets don't get through. I should also configure iptables to only allow packets from trusted external IP addresses. I should also set very strong passwords for authenticating use of these services and use public keys for SSH.

Well this all depends, I run a teamspeak server and ssh server both exposed to the internet (router has that computer in dmz+ mode which means ALL traffic is forwarded to this server) I have ssh configured in a way where it will auto ban ip's that try and fail to connect 5 times. So I really have no need to use iptables to restrict any traffic. This type of stuff will vary with how paranoid the admin is and who you want to allow to access your service.


> **BlakeM said:**
> 
Ok, I've got a few other questions but I'll stop myself here. I'm pretty sure I've got a basic understanding. If any of this is wrong please let me know. I've been reading a lot of stuff on the Security forums. Just need a few things clarified. Thanks for taking the time to read and answer my questions.

P.S. I accidentally posted this in the security forum. I don't think that's where I should have posted so I moved this thread to here. Wasn't sure if I could delete/move threads properly so I've created a duplicate thread. Could a moderator please clean up my mess? Thanks.

---

### Post by BlakeM on 2009-01-26
Ok, thank-you all so much for clarifying those issues. I'm trying to learn as much as possible about Ubuntu and it's a bit overwhelming at times.

---

### Post by BlakeM on 2009-01-26
You're responses have really helped me understand a lot more. I still have a few things I'm unsure about.

Ok, so main difference between a router (i.e. hardware firewall) and iptables (software firewall) is that a hardware firewall either accepts or rejects all packets (depending on whether the a port is open or closed). And a software firewall is able to distinguish between packet types, where the information is being sent from, what IP addresses traffic can be accepted from, etc.

(Out of curiosity: I've heard that one way to compromise a system is to find a fault in the service that's listening on a port...do hackers exploit these vulnerabilities by sending illegitimate packets to these services...or is it way more complicated than that?) 

Man, I feel like a total noob :oops: .

---

### Post by BlakeM on 2009-01-26
> Well this all depends, I run a teamspeak server and ssh server both exposed to the internet (router has that computer in dmz+ mode which means ALL traffic is forwarded to this server) I have ssh configured in a way where it will auto ban ip's that try and fail to connect 5 times. So I really have no need to use iptables to restrict any traffic. This type of stuff will vary with how paranoid the admin is and who you want to allow to access your service.

Ok, so before I install any server-type programs I should probably learn how to configure them properly first?
> 
Without a firewall, it's all or nothing - port is either closed to everybody or open to everybody
With a firewall, it's more configurable and you can write rules for certain IP addresses, packet contents, etc.

As well as learning a few iptables rules.

---

