---
title: "setting up a small network"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-12-04
i am about to take my laptop (running hardy) back to my home and i want to get it networked with two other computers both running windows xp.how do i do so?do i need a router?can the connection be done in case of only two computers with a mere LAN cord and without a router or something?

---

### Post by Zzl1xndd on 2008-12-04
Could you give us a little more information. What kind of set up is there presently? Is it just one Computer connected to the Internet?

---

### Post by stonecoldjha on 2008-12-04
yeah one of those desktops is connected to the internet. i anyways want to share some of my files with the two computers,and also be able to access the internet through this LAN.if i need any hardware for the purpose,i can even restrict networking my laptop to only one of those  computers,if that can be done with a simple LAN cord.

---

### Post by Kellemora on 2008-12-04
HI SC

You CAN connect two computers together without a router, but you need a special LAN cable called a crossover cable.
At the price of those things, your about 1/2 way to buying a router which you will probably end up getting anyhow.  They are not expensive these days either.  You can pick a Dlink up for just under 30 bucks or a LinkSys for around 45 bucks.

Using a router will stop about 80% of the problems in getting your LAN up and running.

You will need to download from Synaptic:
Samba (if not already installed)
SmbClient
and I recommend loading smbtree as well so you can see if your LAN is up and running and seeing the shares, even if Ubuntu is not showing them in places/network, a common problem in Ubuntu.

Also, if smbfs loads with the Samba package, uncheck it so it is removed.  smbfs prevents you from seeing some of the shares.

That's about all I can add for right now!

Good Luck

TTUL
Gary

---

### Post by Zzl1xndd on 2008-12-04
I second what Kellemora said.

A router is probably the best way to go. You can network your computers using a switch or a Crossover cable, But the cost is similar. 

To access the Internet in the configuration you describe (Without a router) you would have to install a second Nic in one of the Windows computers and use Internet connection sharing, but once again that brings us back in the price range of the router. 

So I guess the short answer is buy a router, it will let you network all 3 PC's, Access the internet from all 3, and provided a little extra protection when you are online.

---

### Post by stonecoldjha on 2008-12-04
i have got a device that splits a single uplink LAN connection into 5 downlink connections so that a single LAN connection can be shared among 5 computers.it is basically a switch.how can i use that?

---

### Post by linux_tech on 2008-12-04
Actually a 4port hub and 2 rj45 network cables is all that is needed to connect 2 computers together.  A crossover cable is usually just used for temporary connections. A router (aka Dsl modem) serves to connect computers to the internet and also acts as a hub to network the computers.

---

### Post by Zzl1xndd on 2008-12-04
If its a switch you can use MS Internet connection sharing, but one of the machines will still require Two network cards. As most Nics are 15-20 dollars, I still recomend going with the router. But if you have an extra Nic kicking around or one of the Machines already has Two heres the info.

[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

---

### Post by gpsmikey on 2008-12-04
Definitely go with a router.  It blocks LOTS of incoming junk (port probes etc) it also makes your network easier to set up and configure.  The problem with a switch/hub is that if you have 3 computers for example, each one would need an IP address handed out by your ISP since they are connected directly to the internet (well, cable modem etc).  A router has (typically) a 4 port switch built in AND it does NAT for you which allows any number of machines on the local side (your house for example) to only really require 1 IP address from the ISP since the router converts traffic from the machines in your network such that to the outside world, your 3 machines, each with a browser running only looks like 1 pc with 3 browsers running.  It also keeps your file sharing etc local.

mikey

---

### Post by Kellemora on 2008-12-04
GPSMikey

You just completely answered a question I have had for over 5 years now with no logical answer ever coming forth, and in a way which I understand completely.

My cable provider said I was limited to 4 connections!
Yet I have 8 computers on my LAN (sometimes 9 or 10) and found out right away that they ALL have internet access, all draw their upgrades and updates and I'm often running 4 to 5 on-line at once, yet my ISP only sees ONE of them, I assume the ROUTER after what you just said.  I only have two connections to the Router, one for front office through a Switch of 2 computers.  And the second cat5 to the router is from my back office of 6 computers, through 2 stacked 4 port hubs, actually switches.  Switches work much better than hubs!

I guess it's the IP numbers for each computer and the power of the Router that keeps everything from getting all messed up?

So Thanks for answering a long standing question for me!

TTUL
Gary

---

### Post by gpsmikey on 2008-12-04
Yes, that is correct -- if you go into the router and look at the configuration/status, you will see that on the WAN (cable modem) side, it will have an address like 65.73.23.67 or some number of that flavor.  If you look at the IP addresses of the machines on the LAN (house) side, you will find they typically have addresses like 192.168.2.x or something along those lines.  The 192.168.2.x type addresses are called "private IP addresses".  
More info here: [http://winhlp.com/node/65](http://winhlp.com/node/65) 

The key to this whole thing with these little routers (Linksys, D-Link etc) is the use of NAT (Network Address Translation) which maps the local IP addresses to a port associated with the WAN IP address making everything behind the router look like one computer to the outside.  More on NAT (and PAT) here: 
[http://computer.howstuffworks.com/nat.htm](http://computer.howstuffworks.com/nat.htm)
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

Happy reading !!

mikey

---

