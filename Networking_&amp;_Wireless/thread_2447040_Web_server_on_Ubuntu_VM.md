---
title: "Web server on Ubuntu VM"
date: 2020-07-11
forum: Networking &amp; Wireless
---

### Post by rva2112 on 2020-07-11
I apologize in advance if this isn't the correct forum. My issue involves Ubuntu, Apache, and Virtualbox - so I'm starting here. I hope someone will be generous enough with their time and patience to  help me with what I suspect might be a very simple problem.

**GOAL**:  My ultimate goal is to develop a web application for personal use,  running from Apache on Ubuntu Server within Virtualbox on my Windows 10  host. At a minimum, I need to access this web application from other  devices and VM's within my LAN. Down the road, it would be nice to be  able to get to it from the outside, but that doesn't concern me right  now.

**SETUP**: 
[LIST]
[*]The physical host is a Windows 10 laptop. 
[*]I installed Ubuntu Server on Vbox 
[*]I  installed Apache on the server and the localhost reports an IP of  10.0.2.15, which does in fact load the default Apache page in the  graphical browser within Ubuntu server. 
[*]I installed Ubuntu Desktop as a separate VM in Windows 
[/LIST]
**PROBLEM**:

I  cannot reach the default Apache page from either the Ubuntu Desktop VM  or a Windows browser. In Ubuntu the connection is refused, in Windows it  times out.

**STEPS TAKEN TO RESOLVE**:
[LIST]
[*]I shut down my Windows firewall 
[*]I  have a NAT, a bridged network connection, and a host only connection  all set up on the VM and they all report as being connected. 
[/LIST]
&#8208;------

I'm  not completely ignorant with regard to networking or with linux, but  what I thought would be a routine first step for my project is being  stymied by what I think has to be a simple oversight on my part. I'm  convinced it has something to do with the network setup on Virtualbox or  with the IP address needed to access the server.

Thanks to anyone with some advice here.

---

### Post by TheFu on 2020-07-12
In the VM settings, use a "bridged" network, not NAT.

The virtualbox manual has a chapter on the different network options which explains the multiple different choices and what each means.  You want bridged to have any VM accessible on the LAN by other systems on the LAN.

In the future, if you want to make the webapp available on the internet, I'd strongly suggest NOT using Windows as the host. IMHO, it cannot be secured and the firewall is a toy.  If this is just going to be a personal webapp, don't make it available over the internet. Allow ssh and VPN connections onto your LAN and use those to access any internal only webapps.  I do this for my email server, nextcloud, wallabag, ZNC, and about 10 other webapp systems.  Public facing webapps are placed onto a completely different subnet with firewalling to prevent trusted desktops from getting hacked through them.  And of course, wifi is on a completely different subnet from both the others. Wifi today just can't be secured, sad to say.

If I were doing a fresh webapp today that wasn't going to be a monster, I'd use a container technology - lxd or docker. There are many reasons why enterprises to moving to Linux Containers instead of full VMs.  Put the DB in 1 container, the web-app in another and any front-end web-app stuff in another. This will enable scaling out as needed.

---

