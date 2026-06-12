---
title: "[SOLVED] VitualBox - XP different IP Range"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by cavy on 2008-07-05
Hi Everyone 

Running Ubuntu 8.04 
Running VitualBox 1.6.2 (with XP)

Wired IP on Ubuntu is set to static IP 192.168.0.x, with Gateway 192.168.0.253. which all works fine

VirtualBox XP is assigned to NAT, which generates an IP of 10.0.2.15, Gateway and DHCP server: 10.0.2.2, DNS 10.0.0.2.3. With this configuration i can browse the internet but no dns resolution, also if i access the internet on the Virtual Machine it cuts the internet from Ubuntu, and vise versa

i know very little of all this, but is it possible to have the Virtual windows running on the same 192.168.0.x range? i assume this would fix up the cutting out and i could forward some ports on my Router for the Virtual Machine, or is that just the way it works being a virtual machine?

I have DHCP activated, on my router 192.168.0.253, i have tried static and Dynamic Ip's for both Ubuntu machine.

Can anyone explain to little ol me?

Thanks guys

---

### Post by Jose Catre-Vandis on 2008-07-05
Yes, you need to set up a network bridge on your host and create some virtual NICs to get this to work. Have a read here, should give you everything you need.

[http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/)

It is still current for Hardy

---

### Post by cavy on 2008-07-05
> **Jose Catre-Vandis said:**
> Yes, you need to set up a network bridge on your host and create some virtual NICs to get this to work. Have a read here, should give you everything you need.

[http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/)

It is still current for Hardy


Wow thank you very much, My virtual Machine settings: IP, Gateway DNS, DHCP are all now 192.168.0.x

have DNS resolution on my virtual, and my internet connection is no longer being interrupted by host / slave access.

Thanks again

---

### Post by Jose Catre-Vandis on 2008-07-05
My pleasure :) Please mark this thread as solved

---

