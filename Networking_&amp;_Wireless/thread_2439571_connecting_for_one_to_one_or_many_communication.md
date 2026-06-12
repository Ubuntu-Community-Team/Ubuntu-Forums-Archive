---
title: "connecting for one to one or many communication"
date: 2020-03-29
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2020-03-29
we need (or do we already have?) a standard open (libre) protocol for  distant people who do not (immediately) know each other's IP address  (and may be behind restrictive firewalls or routers) to connect with  each other, over which   such a protocol will need to allow anyone to run a central HTTPS based service (known by their host name or IP address) that can help figure out if any of several ways to directly communicate one-to-one will work.  two people knowing the same host name and same ID string (maybe also password) can connect at nearly the same time to the central server and engage in "direct communication discovery".  if direct communication is possible, then the application doing this can communicate with the other.  this can then enable things from teleconferencing to a VPN (to do many things).  an option would allow an implementation of this to actually carry the traffic between them if no direct means exists (the central service may limit bandwidth, length of time to use, or operating hours).

TCP/IP does not make it that easy for remote parties to communicate (or, at least, find each other) except through servers, especially when their networks are limited.  and so many of these services are very restrictive, costly, and/or demand private info.  an open protocol would encourage open implementations which would encourage many, who can, to offer alternative choices, or allow private groups with networking resources to make better use of what they have.

one alternate option is to just run a central OpenVPN server and share the domain name, port number, IP address, login ID, password, and/or secret key with  colleagues or friends or family.  but this isn't as easy without costly resources like a domain name or server.

this "new normal" will need new thinking.

---

### Post by TheFu on 2020-03-31
Or just use a peer-to-peer VPN.  Check out tinc.  People who are already known to each other can network securely using  RetroShare, but 1 system in the group needs to run a server w/ an open port so all the other systems can find each other from behind their firewalls.

There are some new VPNs that work through cheap, home, firewalls, by tricking the firewall into opening ports between both systems. This is a huge security problem, but it does work.   i don't remember the exact name of the VPN using that method, but it uses the tinc trick. [https://www.tinc-vpn.org/examples/firewall/](https://www.tinc-vpn.org/examples/firewall/)

---

### Post by Skaperen on 2020-04-02
i'm looking at cases where the firewall is controlled by someone else and there is hypothetically some way of limited reach to the internet.

i'm aiming to connect two (or more) people together who do not know their source IP for any reason AND are NOT running their own server (defined as having an IP or domain name (host label with A or AAAA record or CNAME that goes to one) to connect to).  what i'm thinking about is an *arbitrary* third-party (OK, one of the two can play the third) server that can be connected to (shared knowledge how to connect there) where the negotiation starts.  the two parties trying to connect would also share knowledge of an arbitrary unique string that is passed to the negotiation agent (the third party server).  the 2 parties try each others IP at separate times and also at coincident times (i've been able to sneak through a major firewall blockage this way over SCTP though UDP is probably also doable this way).  at that point communication of the connection can begin.  it might be UDP, TCP, or SCTP in rare cases.  then the agent is no longer needed.

it does make sense to prefer a VPN over this.  OpenVPN makes sense but more fudge would be needed if only SCTP works. tinc is an option.  i don't follow that tinc trick since it doesn't show anything about the other party.

one possible way through might involve making the communication appear to be HTTP.  HTTPS is not an option since it is totally hidden to any firewall (it won't know if HTTP is in the encrypted channel or not).  many places just let port 443 through (so try it at some point).  some places might totally block port 443 (perhaps since they cannot spy on it).  i've even heard of places checking to be sure the traffic on port 443 is not some clear text pretending to be an encrypted connection (BTDT).

---

### Post by TheFu on 2020-04-02
i've worked places where desktops had no way to connect to the internet without using the approved proxy.  Those desktops have a company root cert, so all SSL traffic could be inspected.  Any traffic that couldn't inspected is blocked.  PERiod. The company did MiTM w/ all traffic.
if you just want to transfer files, check out wormhole.  Neither party needs to run a server or open any inbound ports.

Ars did a story about a VPN based on tinc that doesn't need any inbound ports, but it only works on weenie firewalls, not the enterpri  se sort.   [https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/](https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/)
> Nebula can&#8212;in most cases&#8212;establish a tunnel directly between two different NATted networks, without the need to configure port forwarding on either side.
But i think 1 system, somewhere in the mesh, must be a server, or there's no way for the nodes to find each other, especially for mobile devices.

---

### Post by Skaperen on 2020-04-03
if tinc can do shared key then i can see how that would work as long a both ends know the IP address of the other end.  but if they don't, that's where my idea comes in.

---

