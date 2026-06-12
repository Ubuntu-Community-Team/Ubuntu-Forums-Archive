---
title: "MyBookWorld on Mac and Ubuntu over Airport Extreme Simultaneoulsy"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by charliedontserf on 2008-08-26
Hi All

I am really impressed with the way Linux has come along in the last few years but I have a tricky problem someone may be able to solve.

The scenario:

I'm trying to use an ethernet MyBookWorld II simultaneously on my MacBook Pro and my Ubuntu box, and route an internet connection from the Ubuntu box all at once. 

My solution:

I'm doing this by connecting to an Airport Extreme router that should serve both boxes with access to it simultaneously.

It should be simple but there's a complication I can't get around – namely I also use it to share my internet connection which is connected to the Ubuntu box and routed to the WAN port of the Airport Extreme and distributed from there wirelessly (and by hard line if need be).

The internet access from the Ubuntu box is fed on eth0 using firestarter to route a 3G Sierra Wireless internet connection into the WAN port of the Airport Extreme router. From here that connection is shared wirelessly to MacBook Pro using FireStarter on eth0. 

The eth0 on my Ubuntu box has the IP 192.168.0.1 fixed and the Airport Extreme accepts its configuration using DHCP from dhcp3 which is directed by firestarter to listen on the IP address.

The Airport Extreme then takes its name server info automatically and sets its WAN port IP in the address range 192.168.0.x. - usually -.17 or something safe.

It then issues addresses from there in the subnet range 10.0.1.x using DHCP and servers its own router address as 10.0.1.1.

That all works very nicely and I can distribute the connection to my MacBook and my iPhone which take one the gateway address 10.0.1.1.

Goal one achieved.

Goal two hits a problem.

The MyBookWorld can be seen by the Airport connection on my MacBook Pro because it automatically takes on the router gateway information as 10.0.1.1 and automatically sees the SMB/CIFS location and shares (as MyBookWorld is essentially an SMB server I believe)

But the Ubuntu box can't do this because it messes with the DHCP activity and name server addressing of the 3G connection.

On a Windows XP box you can pretty much have an identical arrangement setup and get around the problem by using a second ethernet card to reconnect to the Airport Extreme router and give it a fixed IP in the 10.0.1.x range. It just seems to find the MyBookWorld box  - probably taking the gateway information without screwing up the native internet connection sharing.

I find that with the same arrangement in Ubuntu, if you give the eth1 a fixed 10.0.1x IP and set the gateway (Airport Extreme Router) as would under Windows, you get mixed results finding the  SMB/CIFS shares on MyBookWorld (usually works) but it messes with the name server arrangements for the 3G connection and it can't resolve hosts properly.

Goal one goes out the window.

Does anyone have a suggestion for how I might be able to fix this problem?

Any help appreciated in advance.

CDS

---

### Post by charliedontserf on 2008-08-30
Yeah, okay I'll wear it. I'm an idiot.

A friend helped me out with this.

For anyone who cares, you can set up airport extremes in bridge mode. 

That way when firestarter starts listening in on the port and assigning dhcp3 it it just gives out addresses and so on to anything that joins the airport.

I am dumb. It's confirmed.

---

