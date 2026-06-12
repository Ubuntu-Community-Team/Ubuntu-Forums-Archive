---
title: "SSH Directly over ethernet"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by twtduck.ii on 2015-01-17
I have two laptops, and would like to ssh to one from the other. However, my work network doesn't allow any communication between devices on the network, other than the internet, so I grabbed my handy ethernet cable and connected the two manually (no router). I've set up the connection to use the following static ip settings:

Laptop 1:
[LIST]
[*]IPv4: 192.168.13.0 
[*]Subnet mask: 255.255.255.0 
[*]Gateway: 0.0.0.0 
[/LIST]

Laptop 1:
[LIST]
[*]IPv4: 192.168.13.1 
[*]Subnet mask: 255.255.255.0 
[*]Gateway: 0.0.0.0 
[/LIST]

I can't even ping between the computers, so I have some sort of issue with my connection settings, though I don't know what. Thank you for responding.

---

### Post by The Cog on 2015-01-17
You cannot use 192.168.13.0 - it is the "network" address and is reserved. Try using 192.168.13.2 instead.

Connecting two laptops directly will require a "crossover" cable instead of a normal ethernet cable. In the output from the command "ifconfig", look for the word RUNNING. If you don't see RUNNING then the cable is probably not right.

---

