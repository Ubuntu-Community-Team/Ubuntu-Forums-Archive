---
title: "Setting up a home server"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Natrilix on 2010-04-15
Hi all,

I've been using Ubuntu as my desktop OS for a while now, and am really loving it.

However, I recently moved into an apartment block with 10 of my friends, and we all share a wireless network and internet connection. We have quite fast internet access, advertised as 50Mb/sec, but one of our number is a real badwidth hog. She constantly streams video, downloads hundreds of things at once and and uses p2p software 24 hours a day.

We've spoken to her about it, but after a month of this we've all decided to limit her bandwidth. From looking around the web it seems the best way to do this, short of buying a new router with better QoS (we have a D-Link DIR-615), is to set up a small server. Since I have an old computer lying around, and would quite enjoy taking on the project anyway I volunteered to do it.

So, with that out of the way, my main questions are:

[LIST]
[*]What is the best way to limit the bandwidth of one user on the network?
[/LIST]

[LIST]
[*]Is it possible to have such a system that will be invisible to other users. That is to say, could we have a server that interferes with traffic that no one would have to log into to access the interent, other than the WPA key for the router? Everyone would prefer this server to cause as little disruption as possible.
[/LIST]
Or am I simply going about this in an over-complicated way? I'm open to other suggestions about solving the bandwidth problem, though I would quite like to set up a server anyway.

Thank you!

---

### Post by Paqman on 2010-04-15
There's a package for the server called squid that can be set up as a transparent proxy. It can do just about anything, including restricting bandwidth.

It's a bit geeky to set up, but is pretty widely used, so you should be able to find plenty of help with specifics.

---

### Post by undecim on 2010-04-15
I think a new router is best suited to fix this situation if you can afford it. I have a linksys home wireless N router and I am able to run p2p 24/7 on a 10mpbs connection with almost no effect on anyone else on the network.

If you want to go the server route though this question might be better to ask in Server Platforms or Networking and Wireless (ask a mod to move the thread for you)

---

### Post by Gone fishing on 2010-04-15
With Squid you can also use Sarge and see exactly how much people have down loaded what site they've been to etc. Possibly a little scary!

You can set up restrictions to use etc etc. 

I use Webmin which makes setting up squid fairly easy.

---

### Post by mk1w86 on 2010-04-15
From the requirements you've listed a dedicated firewall distro such as IPCop:

[http://sourceforge.net/apps/trac/ipcop/wiki](http://sourceforge.net/apps/trac/ipcop/wiki)

or Smoothwall: 

[http://www.smoothwall.org/](http://www.smoothwall.org/)

might be better suited to your requirements.

There is also M0n0wall which is BSD based:

[http://m0n0.ch/wall/](http://m0n0.ch/wall/)

---

### Post by Natrilix on 2010-04-15
Thanks very much everyone!

Really great response, and some fantastic advice.

Any help on how to make sure the server isn't disruptive to anyone on the network? Much as my faltmates want faster internet, they really don't want to have any extra work or log in screens.

---

### Post by mk1w86 on 2010-04-15
> **Natrilix said:**
> Thanks very much everyone!

Really great response, and some fantastic advice.

Any help on how to make sure the server isn't disruptive to anyone on the network? Much as my faltmates want faster internet, they really don't want to have any extra work or log in screens.

The server shouldn't cause any disruption or require a login unless you set it to so your flatmates should be able to access the internet as they would normally.

Another thing though, I've just re-read your original post, specifically this part:

> Is it possible to have such a system that will be invisible to other users. That is to say, could we have a server that interferes with traffic that no one would have to log into to access the interent, other than the WPA key for the router? Everyone would prefer this server to cause as little disruption as possible.

Normally, for the setup you are looking at, the server would have at least two network interfaces and the router would be 'behind it' (connected to one interface) and all the machines would be connected 'in front' of it (to the second network interface).  This means all traffic flows through the server so you would not be able to use the wireless built into you router because that effectively bypasses the server.  The way round this would be to have a separate wireless access point 'in front' of the server which is what everyone would connect to.  I have attached a diagram of an example IPCop setup (but it should apply to whatever distro you choose) which is probably easier to understand than my explanation. ;)

---

### Post by egalvan on 2010-04-15
> **Natrilix said:**
> .

edit, wrong message

---

### Post by Natrilix on 2010-04-16
> **mk1w86 said:**
> Normally, for the setup you are looking at, the server would have at least two network interfaces and the router would be 'behind it' (connected to one interface) and all the machines would be connected 'in front' of it (to the second network interface).  This means all traffic flows through the server so you would not be able to use the wireless built into you router because that effectively bypasses the server.  The way round this would be to have a separate wireless access point 'in front' of the server which is what everyone would connect to.  I have attached a diagram of an example IPCop setup (but it should apply to whatever distro you choose) which is probably easier to understand than my explanation. ;)

OK, I think I get it. Based on your diagram, in my current setup, I would only be using the "Blue" line. I take it my computer would need two network cards, and therefore two ethernet ports (which it does have actually)?

---

### Post by mk1w86 on 2010-04-17
> **Natrilix said:**
> OK, I think I get it. Based on your diagram, in my current setup, I would only be using the "Blue" line. I take it my computer would need two network cards, and therefore two ethernet ports (which it does have actually)?

You would probably be better off using just the green network which is compulsory on IPCop, so to use blue you would require a third network card.  The main function of the separate zones is to isolate each one from each other e.g. users on the blue network would not be able to access machines on the green network.  The reason behind this is if someone hacked into your wireless for example (which is less secure than a wired network), they cannot access the machines on the 'safe' green network, the same goes for orange which is designed for internet facing machines.

Here is an explanation of each zone from the IPCop installation manual:

**1.2.1. Network Interfaces**
IPCop defines up to four network interfaces, RED, GREEN, BLUE and ORANGE.

**1.2.1.1. RED Network Interface**
This network is the Internet or other untrusted network. IPCop’s primary purpose is to protect the GREEN, BLUE
and ORANGE networks and their computers from traffic originating on the RED network. Your current connection
method and hardware are used to connect to this network.

**1.2.1.2. GREEN Network Interface**
This interface only connects to the computer(s) that IPCop is protecting. It is presumed to be local. Traffic to it is
routed though an Ethernet NIC on the IPCop computer firewall.

**1.2.1.3. BLUE Network Interface**
This optional network allows you to place wireless devices on a separate network. Computers on this network cannot
get to the GREEN network except tightly controlled “pinholes”, or via a VPN. Traffic to this network is routed through
an Ethernet NIC.

**1.2.1.4. ORANGE Network Interface**
This optional network allows you to place publicly accessible servers on a separate network. Computers on this
network cannot get to the GREEN or BLUE networks, except through tightly controlled “DMZ pinholes”. Traffic to
this network is routed through an Ethernet NIC.

**1.2.1.5. Network Interfaces**
Your firewall will need at least 1 Ethernet cable and network interface card (NIC). It may need up to 4 NICs, depending
on the network configuration you choose and your connection to the Internet.
All NICs must be different physical cards (or their equivalent if you have multport cards).
Ignoring for a moment the RED network, you will have to plug a separate Ethernet NIC and cable into your firewall for
each of the GREEN, BLUE and/or ORANGE network. The GREEN and RED networks are required. The ORANGE
and BLUE networks are optional. The interface requirements for your RED network will vary depending on your
connection to the Internet. The RED network may require an additional Ethernet card and cable.

My IPCop setup is just the red and green interfaces, I have an ADSL modem connected via ethernet to red and a wired ethernet network switch connected to green, I then have a wireless access point plugged in to the switch so all wired and wireless machines can see and access each other.

All this is obviously for an IPCop setup but whichever firewall distro you choose will probably have a similar setup. ;)

---

