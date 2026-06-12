---
title: "Two NIC cards"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by manoy on 2008-05-28
hi, I need help, I installed 2 NIC cards and I want one to connect to the internet (obtain IP Address) and the other one to connect to my local windows xp network (Static IP) without sharing the internet connection to my local network. I have no idea on how to do this. thank you in advance :)

---

### Post by Koffee Kid on 2008-05-28
I need help with this as well,cept I use ubuntu studio.

Mike:confused:

---

### Post by pricetech on 2008-05-28
Sounds like fun.  OK, here's what I have in three computers; (2 Ubuntu and one XP)  I'll use my main workstation as the example as they are all pretty much the same basic configuration.

Onboard NIC is on the Internet, connected through an ISP provided modem / router.  I'm using a fixed IP, but could just as easily use DHCP, so we'll say that I am.  It allows me to connect to the Internet but its connection is not shared.

Second NIC is on an internal network.  It has a fixed IP but does not have a gateway assigned.  This keeps my computer from trying to find the Internet via that interface.  I use it to connect to internal servers and workstations for various reasons.

My IP configuration goes like this:
ETH0:  DHCP
It gets an IP Address, Subnet Mask, Default Gateway from the DHCP server.  My computer will attempt to reach any and all destinations via that interface unless I specifically instruct it otherwise. (keep this in mind for later)
ETH1  Fixed IP
IP Address is 192.168.10.115, Subnet Mask is 255.255.255.0 and the Default Gateway is blank.  This keeps my computer from trying to reach destinations via this interface.  It will attempt to reach anything in its own subnet, but otherwise will use the default gateway assigned by the DHCP server.

If all you want to do is what you described, then this should be enough information to get you going.

Obviously you'll need to assign your fixed IP according to the subnet where your windows computer is located.  Just make sure you leave the Gateway entry blank on this interface.

Best of luck.

---

