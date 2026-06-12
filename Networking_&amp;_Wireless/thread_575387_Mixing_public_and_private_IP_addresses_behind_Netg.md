---
title: "Mixing public and private IP addresses behind Netgear FVS318"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by bramint on 2007-10-14
I am running ubuntu Feisty
my lan setup is like this:
DSL modem
Netgear FVS318
several PC (windows and Linux)

I have a linux PC that I have two NICs.  I want one for the local LAN 192.168.*.* subnet 255.255.255.0 and one that goes out over the Internet with a public IP address 72.36.*.* subnet 255.255.255.248.  The building is wired to have all connections go through the FVS318 with no possibility of connecting the second linux NIC directly to the DSL Modem for the public address.

How can I have one NIC which goes through the FVS318 work with a public address and by pass the firewall of the FVS318 while still going through the FVS318?

I can't ping the DSL because it is on a different subnet than the local lan.

Any ideas?

Thanks

Joe Saladino
[email]joe@bram.net[/email]

---

### Post by SpiritIsReality on 2007-10-28
howdy
I don't know for sure, but
I know that in this area with telus, the internet service provider, and the package we have, that we are allowed 2 public addresses. I imagine it would take another dsl modem.
The linux box could be plugged directly into the second dsl modem, and the public address would be assigned to the external nic?
trails

[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
[http://linux-ip.net/html/index.html](http://linux-ip.net/html/index.html)

---

