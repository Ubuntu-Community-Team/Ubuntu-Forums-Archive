---
title: "Clone packet with iptables"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by SundaY82 on 2007-02-20
Hi,

I have a service on both the computer that acts as the router and one on the local network using the same port. Is it possible to clone the packet that comes in so both the router computer and the internal computer gets the packet?

To make it a little clearer the service is glftpd and i want to use ident(113) on both the router box and the internal box.

Is there a way to solve this?

right now i only have this line for port 113:
$IPT -A INPUT -i $WAN -p tcp --dport 113 -j ACCEPT

and that offcourse makes it work for the router box but i need to make a copy of the packet and send to the internal box also so it will work there too.

---

### Post by koenn on 2007-02-20
I think you'd need to explain **why** you want this or what purpose you have in mind

---

### Post by SundaY82 on 2007-02-20
> **SundaY82 said:**
> To make it a little clearer the service is glftpd and i want to use ident(113) on both the router box and the internal box.
I thought that explained it, or what do you want me to explain further?

---

### Post by koenn on 2007-02-20
OK - 
you say you want a packet to arrive both at your router and at an other PC. 

I'd say : connect both the router and the other pc to a hub - they will both see all packets. 
The purpose of that could be you want to run a protocol analyser to study the traffic coming to the router. 

Or : you want to run an FTP service simultanously on the router and on an other pc. That sounds rather weird, so i'm wondering : what does this guy want to do ? Like : if a packet arrives to both the router and the other computer that contains an ftp "get" statement, should the file be downloaded from the router ? from the computer ? from both ? 

Maybe you're just trying to route traffic to an ftp server behind a nat router, but that has nothing to do with cloning packets. 

Or ...

So - care to explain ?

---

### Post by SundaY82 on 2007-02-20
> **koenn said:**
> OK - 
you say you want a packet to arrive both at your router and at an other PC. 

I'd say : connect both the router and the other pc to a hub - they will both see all packets. 
The purpose of that could be you want to run a protocol analyser to study the traffic coming to the router. 

Or : you want to run an FTP service simultanously on the router and on an other pc. That sounds rather weird, so i'm wondering : what does this guy want to do ? Like : if a packet arrives to both the router and the other computer that contains an ftp "get" statement, should the file be downloaded from the router ? from the computer ? from both ? 

Maybe you're just trying to route traffic to an ftp server behind a nat router, but that has nothing to do with cloning packets. 

Or ...

So - care to explain ?i only want to "clone"(may be a better word for it) the packages to the ident port, ie 113 so i can use ident on both my ftp servers. So both the router computer and the internal computer get the ident request.

---

### Post by koenn on 2007-02-20
Isn't identd supposed to be running _on the clients_ then, so that both ftp servers can resuest user identification from it ? (Or am I getting that wrong ?)

---

### Post by SundaY82 on 2007-02-20
> **koenn said:**
> Isn't identd supposed to be running _on the clients_ then, so that both ftp servers can resuest user identification from it ? (Or am I getting that wrong ?)I dont know exactly how ident work but its the ident response from the client has to reach the ftp server somehow so it knows its correct, or have i got it all wrong?

Its not working on the internal computer so must be something.

---

### Post by koenn on 2007-02-20
it will reach the server that requested the ident - i.e. the reply will be send to the (address of) the (ftp) server that requested it. Your problem then is one of routing with most likely some NAT. 

post the ip address of that internal ftp server and I'll have a look at it tomorrow, if noone steps in before that.

---

### Post by SundaY82 on 2007-02-20
ok, thx for clearing that up. The routing of the ftp port and data ports for the ftp works great so no problem there. So it must be something broken on the internal ftp server box with identd?

So it works like ping from the server side, the router knows who requested the ping and forwards it corerctly to that box. And ping works so then ident should work too.

---

