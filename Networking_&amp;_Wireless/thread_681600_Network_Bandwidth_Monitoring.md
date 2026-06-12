---
title: "Network Bandwidth Monitoring"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by apothecaryaaron on 2008-01-29
Background:  My office is preparing to move to another location.  We have more options for Internet connections at the new building.  Currently, we are sharing a T1 with our sister company.  My boss has asked if there is a way to monitor the bandwidth of the computers of my side of the company.  I'm sure I could pull this off in Windows if I tried, but I really really really enjoy bringing in my 'buntu laptop and making things work.  
 
Stuff I know:  We have 3 main computers (the rest don't use enough to count) that run through a 5 port switch.  I have the internal IP of that switch.  Everything outside of that belongs to the sister company (a daytime pharmacy with 20+ computers), so I assume we don't want to mess with that bandwidth, as they are staying put.  I can also easily get the internal IP's of our 3 mains fairly easily.
 
What I need:  Something that will monitor bandwidth usage of our side of the T1.  I need only to be able to get average usage of up and down, no detailed information.  Actually, due to the kind of data we transfer, the LEAST amount of detail would be easier on me.
 
Any advice at all would be appreciated.  It's very fun to show a Windows based "IT expert" how to do things on his network.

---

### Post by rklauco on 2008-01-29
Well, there seems to be some unclear parts in your post.
My first question - 5 port switch has an internal address? I was not aware about possibility to have an address of the switching device in case of not-managed router...
It seems to me that you have not realy a switch device, but a router, connecting your computers using single wire to the main internet connection.
To measure the network traffic from your machine, you can use following command:
```
sudo iftop
```
In case iftop is not installed, install it using following command:
```
sudo apt-get install iftop
```
Anyhow, this command allows you to watch only the traffic going out from your interface, not from the other computers on the network.
If you are using switch, it is a bit difficult to listen to the traffic on the network.
The easiest way is to use traffic management on the router - e.g. Asus WL500g with OpenWRT can trace the current traffic, log the interface activity, etc.
Please, try to be more specific on the hardware of your network - otherwise there is no simple answer...

---

### Post by apothecaryaaron on 2008-01-29
The hardware I am calling a switch is this (or a previous generation of the same).  I don't know what else to call it. [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416836711&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3671145678B03](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416836711&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3671145678B03)
The ip address comment comes from a ping route trace.  I pinged my email server, and the route went from my computer, to an unknown IP, to the server, then back through the steps to me.  The only physical network object between me and the mail server is that switch.  It is very possible there is a virtual something or another that I know nothing about, I am just a pharmacist who likes to learn by trying/asking questions, and have no training except the all-knowing Google.
As far as being specific on my hardware, I did not set this up to have that information at hand.  I do have access to the physical equipment, and passwords, etc are available if I ask.  However, I have to make a trip into the basement, and I have to do it during work hours, so I was waiting to see what information was requested in responses before I descended into the muck. 


I'll tell everyone what I thought would work and give everyone a good laugh at my weird way of thinking.  I was planning on sticking my box with 2 network cards in the line on the other side of the switch(switch >>My comp>>Rest of LAN), and bridging the connections between the network cards.  I know it would slow us down some, but I could monitor traffic through that box and get the approximate usage of my group.  I can do this in Windows easily, but, like I said, why would I want to do that?

---

### Post by rklauco on 2008-01-29
Well, the idea of yours is not bad.
I am not sure if it will slow down your network. Anyhow, routing 100Mbit is a different story, but simple bridging could be a solution.
And, using this setup, you can monitor the connection from your computer to the network and get the statistics you'd like.

The device you described realy is a switch. But, if there is something in the way, it is not the switch - means it has no physical address, it is used as "simple" switch.
According my opinio, between your office and the internet, there will be some routing device (probably the connection from your switch ends up in a router of the network provider) and that is the address that came back from your traceroute command.

Anyhow, the idea of yours could be the right one and can solve the task you have.
The setup is not very hard, you can even use firestarter frontend to setup simple connection for the remaining network and monitor the traffic.
I will (later this day) take a look into the repository - I am sure there is MRTG available, which can do your job rpetty nice, but there should be simplier solutions with less setup and configuration...

---

### Post by apothecaryaaron on 2008-01-29
> **rklauco said:**
> 
The device you described realy is a switch. But, if there is something in the way, it is not the switch - means it has no physical address, it is used as "simple" switch.
According my opinio, between your office and the internet, there will be some routing device (probably the connection from your switch ends up in a router of the network provider) and that is the address that came back from your traceroute command.

 
The IT guy says that there is nothing between me and the server except the switch. However, reality says that you are absolutely correct. I followed the lines down to the server, and sure enough our switch leads to port 2 of a router and the mail server is in port 4. There's my mystery IP. 
 
Thanks for looking into this so far. It's nice to know I'm at least on the right track.

---

### Post by rklauco on 2008-01-30
Congrats on not letting you fooled by "The IT guy" :-)
I checked multiple solutions yesterday, 2 of them I am still testing and will let you know.

---

### Post by apothecaryaaron on 2008-01-30
Thanks. 
 I am looking at ibmonitor.  I have to get home and try it out, but I think it should provide me with enough info for now.  The fun part is going to be bridging the two connections in Ubuntu.  Is that something I should figure out easily, or should I start searching for guides?

---

