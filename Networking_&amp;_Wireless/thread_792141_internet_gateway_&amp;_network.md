---
title: "internet gateway &amp; network"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by longcatspace on 2008-05-12
hi, i'm a complete newbie at ubuntu, please forgive my perhaps obvious questions...

so, i've got 2 PC's and a Mac in the house, currently one of the PC's (both with XP) acts as an internet gateway to the other 2 computers...

i want to set up the internet gateway PC with ubuntu, so it has to be able to be an internet gateway for the other 2 computers and have a working network with the other computers...

i hope this makes sense... i'm close to installing ubuntu on this PC as a dual boot with XP, once i've configured it right i'll abandon XP... 

any help would be much appreciated x

---

### Post by SgtDude on 2008-05-12
I'm not trying to turn you away from your idea, as I think it's a good one.  However, it's not going to be as easy to set it up in Ubuntu as it is in Window$.  On the plus side, though, it will be much more secure.

Basically what you've got right now is a Windows box acting as both a NAT Router and a DHCP server.
NAT = Network Address Translation
DHCP = Dynamic Host Control Protocol

NAT takes one "real" IP address (which is probably automatically assigned by your ISP through DHCP), and lets *n* private (fake) IP addresses get internet traffic through it.

DHCP is a server that accepts requests for IP addresses broadcast by a system as it boots, and responds with a valid IP address, along with other information (Subnet mask, Default Gateway, DNS server(s), etc).

Ok, sorry.  I'm getting a little long-winded.  Basically, you'll want to learn how to use iptables.  It's already installed on your system, you just need to learn how to configure it.  I'm no expert on iptables, though, so I'll refer you to google.  If anyone knows of a good GUI for iptables, please post.

---

### Post by longcatspace on 2008-05-12
thanks, that's a good start x

---

