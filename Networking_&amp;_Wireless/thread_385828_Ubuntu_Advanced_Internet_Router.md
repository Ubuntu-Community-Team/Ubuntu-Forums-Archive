---
title: "Ubuntu Advanced Internet Router"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by goodevil on 2007-03-16
Hi to all

I'm trying to setup an Ubuntu Proxy/Filter Server for network monitoring and administration.

I installed Ubuntu Edgy (6.10) on the server box with squid and dansguardian.
All http traffic is redirected from port 80 -> 8080 to be filtered by dansguardian.
It rocks :guitar:

But my problem is that I want Ubuntu to serve has a transparent router for all other traffic, filter http but allow all other traffic for example MSN, VOIP, etc. 

Here's the network diagram

[ATTACH]27544[/ATTACH]

PC 1 and 2 are filtered users on the 192.168.1.x network.
PC A is the unrestricted user on the 192.168.0.x network.
The server has 2 interfaces eth0 and eth1 and is running squid, dansguardian, ipmasq, dnsmasq.
The router manages the 192.168.0.x network and the server manages the 192.168.1.x network.

Ubuntu is already configured has a router but I'm having problems with iptables, I can´t get PC 1 or 2 to ping PC A or any internet address. But PC 1 and 2 can resolve addresses so I figure dnsmasq is fine.

Now, how can I configure iptables to allow communication between these two networks and of course the internet.

Thanks in advanced.

---

### Post by Catsworth on 2007-03-16
[Offtopic]
Sorry to ask a question without offering any help, but what software are you using to create that network diagram?

Thanks.
[/Offtopic]

---

### Post by goodevil on 2007-03-16
Nop this isn't generated automaticly, I used GIMP ;)

---

### Post by Catsworth on 2007-03-16
> **goodevil said:**
> Nop this isn't generated automaticly, I used GIMP ;)

Ah, ok - thanks.

---

