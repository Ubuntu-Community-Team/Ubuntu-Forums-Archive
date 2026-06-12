---
title: "VMWare xp box not able to ping it"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by twistedtwig on 2007-09-06
Hi all,

I have a couple of servers and a number of work stations in my office.  Call server1 as the main server that deals with dns dhcp and the net access.  Server2 is a real time image of the first from inside the network.

I have installed VM Server onto server2 and created an xp box with it.  This side of things worked just fine.  The xp box loads and using a bridge connection I get an IP address in the same range as everyone else and can see the net and ping other computers by IP address (can't remember at this moment if I could get their computer names to resolve, I think it did but not 100% sure).  The problem is that no one else can ping or connect to that box.

How can I fix that?  The idea of this VMWare is to move an application off of a single box and put it in a place were others can remote onto it (mstsc).

Thanks in advance

---

### Post by scxtt on 2007-09-06
firewall blocking echo requests on XP VM?

---

### Post by twistedtwig on 2007-09-06
hadn't thought about that.. seems a bit odd but hey its XP.. will have a fiddle with that.

Thanks

---

### Post by scxtt on 2007-09-06
i didn't think the firewall was enabled by default - but it's easy to check ... i turned it off on my Server2k3 VM and was then able to ping ... i have an XP VM too and use a bridged connection (IPs off the router) and connect to them via Remote Desktop Connection all the time :)

---

### Post by twistedtwig on 2007-09-06
ahh cool.. not on site at the moment but will check soon.. hope that is the case and will be a VERY Happy bunny.

Cheers again :D

---

### Post by twistedtwig on 2007-09-06
Perfec!!!!!!

Thanks so much all working a treat now, apart from the VM box name doesn't get resolved not sure why really. it can resolve other peoples name but others cant resolve his.  I can set a static IP but seems a bit Naf way of doing it really.

---

### Post by scxtt on 2007-09-06
the DNS server is in charge of that - has it been updated w/ the IP/hostname of that VM?

---

### Post by twistedtwig on 2007-09-06
not manually I thought (possibly incorrectly) that it did that automatically. The dhcp and dns are on the same box I thought when it gives out a new IP it does the dns at the same time (sbs2003 box)

---

### Post by scxtt on 2007-09-06
i'm not sure about the particulars on a DNS server - never had cause to set up my own - all i know is when we create new hosts (physical or virtual) at work, we have to request a DNS update for any IP that would be resolved from a hostname ... i suppose there could be a DNS server convention that goes out and *crawls* the network trying to match up IPs and hostnames in order to update ...

---

### Post by twistedtwig on 2007-09-07
I will have to have a good poke around the server I think to see what the settings are.  Might just set it to a static IP and manually add the DNS record to the server.

---

