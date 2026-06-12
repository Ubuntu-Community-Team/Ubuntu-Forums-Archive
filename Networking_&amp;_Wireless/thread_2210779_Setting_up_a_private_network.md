---
title: "Setting up a private network"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by vitor4 on 2014-03-12
Hello, I need some help for my University final project.

I'm a complete newbie when it comes down to networks so I need a little of help.
To put it simple, I want to setup my own private network (**no Internet access**).

I was given: 3 PC's, 1 Switch with 24 Ethernet ports, RJ-45 Ethernet Cables.

I was thinking about installing Ubuntu Desktop on 1 PC and install LAMP on it so I could run that PC as a webserver.
The thing is that this private network won't have any Internet access at all, so I talked with my teacher and he told to configure the webserver manually by giving IP addresses, netmasks, etc.. to the machine. 

How can I do that?

Do I have to connect a RJ-45 Ethernet cable to a port in the switch and to the PC?

Also, after configuring that webserver, how can I access its content from another computer that is on this network?

Sorry if these questions sound dumb to you, but I really don't understand much about networks, so if you could explain things in a simple way I'd be much appreciated. Thank you.

---

### Post by Lars Noodén on 2014-03-12
One way would be to set up the machine as a DHCP server.  To do that you would put a fixed ip address on the network interface connected to the switch.  Then you would configure DHCPd to use that address, either via Dnsmasq or isc-dhcp-server.  Then, if everything is set up ok, you should be able to connect the other machines to the switch and get an address and then connect to the server.  It's all self-contained.  I'd kind of recommend dnsmasq there since you can also use it to assign hostnames to ip addresses.  That and it's very simple to configure.

---

### Post by wildmanne39 on 2014-03-12
Your thread was closed because the forum has a strict policy against homework threads!
Thanks

---

