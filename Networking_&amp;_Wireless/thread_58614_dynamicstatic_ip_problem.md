---
title: "dynamic/static ip problem"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by Brad wilkinson on 2005-08-20
Ok, this may not be a problem with Ubuntu, but I'll try here first...

I have a Billion 7402 adsl modem/router. when I connect to the router then the internet with dhcp server enabled in the 7402, no problems. 

When I set the dhcp server in the Billion to give the PC a static IP based on the NIC address 00:34:34:whatever it still gives the pc a random address from the list, not the one specified.

The Ubuntu setup is just set to look for the DHCP server.

Any ideas about what I am missing?

---

### Post by nad on 2005-08-20
You need to edit the /etc/network/interfaces file to tell the system your address resolution method at startup. If dhcp is enabled, it will use dhcp.

Once started, you may use the ifconfig utility to set your local address.

Either way, if dhcp is disabled, it will be your responsibility to correctly set the netmask and gateway address as well as confirm your DNS addresses and route.

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=nad]You need to edit the /etc/network/interfaces file to tell the system your address resolution method at startup. If dhcp is enabled, it will use dhcp.

Once started, you may use the ifconfig utility to set your local address.

Either way, if dhcp is disabled, it will be your responsibility to correctly set the netmask and gateway address as well as confirm your DNS addresses and route.[/QUOTE]
I think the OP is suggesting he wants to use DHCP, but he has his router set up to hand out a specifc IP address to his Ubuntu box based on the MAC address of the NIC.  For some reason it doesn't seem to be working.

What kind of output do you get from the "dhclient" command?  Maybe that will shed some light on the situation.  Make sure tere's no typo in the MAC address.

---

### Post by Brad wilkinson on 2005-08-21
well it is sort of sorted now.

I just set the router to dhcp, but no entry based on the MAC address of my machine in question.

went and set the static IP on the PC itself, and now it is showing up as the static IP on the router. I pinged it from my other pc's as well.

so it works now.

not that I fully understand why, but working is working.

now I can get back to trying to configure apt[COLOR=Red][SIZE=7]-**proxy**.[/SIZE][/COLOR]

edit proxy not cache........

---

### Post by heimo on 2005-08-21
[QUOTE=cwaldbieser]Make sure tere's no typo in the MAC address.[/QUOTE]

I second this one. And be sure you have correct separator / format (I don't know about user interface on that particular device), it could be - (dash) or : (colon) or without separator.


EDIT: Bad timing. :) Good it works now.

---

### Post by nad on 2005-08-21
My point being, why have a dhcp server continually offer the same address when the dhclient requests an offer.

It just seems like you are asking for problems. It is certainly easier, with less network traffic to just assign your computer a static address.

---

### Post by heimo on 2005-08-21
[QUOTE=nad]My point being, why have a dhcp server continually offer the same address when the dhclient requests an offer.

It just seems like you are asking for problems. It is certainly easier, with less network traffic to just assign your computer a static address.[/QUOTE]

On a small home network - I don't see the point either (there may be something, I don't know), but for consistency, it may be quite useful if static ip address is needed and you still want to take advantage of other stuff DHCP can configure for you.

---

### Post by nad on 2005-08-21
[QUOTE=heimo]On a small home network - I don't see the point either (there may be something, I don't know), but for consistency, it may be quite useful if static ip address is needed and you still want to take advantage of other stuff DHCP can configure for you.[/QUOTE]

Netmask, gateway and DNS yes, if you are ignorant of the necessity of these.

In a dynamic environment you use _dynamic_  host configuration protocol. This requires the use of a WINS or NIS server to resolve hostnames to dotted quad addresses (NETBios in a peer to peer network, but let's not get into it's instabilities here).

In any size network, the use of a hosts file greatly increases the stability and robustness of the network, decreases network traffic and makes it a breeze to be able to connect to any specific computer by hostname. Certainly one of the main uses of a static address especially in a home or SOHO environment where a dedicated nameserver is overkill.

Software in many of these network devices is often buggy. Why depend on a mass produced piece of hardware/software when the tool at your fingertips is significantly more refined, stable, powerfull and configurable?

---

### Post by heimo on 2005-08-21
[QUOTE=nad]
In a dynamic environment you use _dynamic_  host configuration protocol.[/QUOTE]
Agreed. :)  But I quite can't agree on the advantages of using hosts files on networks of any size, though. (I think I need to get more experience on that side.)

---

### Post by nad on 2005-08-21
The whole purpose of DNS is to be able to connect to a specific computer by canonical name. A DNS server simply resolves fully qualified domain names to dotted quad addresses. A hosts file empowers your computer to be a DNS server for itself.

If all we had to use were dotted quad addresses, we would all have lists taped to our monitors of web site and computers addresses by dotted quad only.

It is the same with the "Connect to Server" dialog in ubuntu. Being able to enter a hostname is certainly easier to remember than its numerical address.

---

### Post by heimo on 2005-08-21
Thanks for explaining. ;)

---

