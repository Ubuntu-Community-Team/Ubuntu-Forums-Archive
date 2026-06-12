---
title: "Understanding addressing"
date: 2018-08-30
forum: Networking &amp; Wireless
---

### Post by vysero on 2018-08-30
I am trying to understand the difference between my inet addr and a LAN address. A guide I am attempting to follow says: "Then add the following line to /etc/exports (change xx.xx.xx.x/xx to match your local network): 
/exports/rfs_dir_for_embedded_device xx.xx.xx.x/xx(rw,no_root_squash,async,subtree_check)". So is the LAN address just going to be my inet addr followed by a / and two numbers?

---

### Post by The Cog on 2018-08-30
An IP address with a slash afterwards (e.g. 192.168.0.101/24 which is the address of the PC I'm on now) indicates two things. There's the address itself (before the slash) and the number after the slash indicates how much of the address (24 bits in my case) is the network address (think of it like an area code). The rest of the address (8 bits in my case) is the host address within that network. So in my case, my network is 192.168.0.* and the host number on that network is 101. PCs need to know how much of their address is local so they know when to try to talk directly to other addresses (like 192.168.0.123) and when the destination is out-of-area and therefore to send the message to the router to be forwarded elsewhere. 

You can get to see your local address with the command "ip address list", or "ip a" if you're feeling lazy.

This is probably different to your public internet address because to get to the internet you are probably passing through a router that does Network Address Translation. But as you are being asked to give the subnet mask (/24) they almost certainly want your local LAN address.

---

### Post by SeijiSensei on 2018-08-30
Internet addressing uses a combination of a network prefix and a "subnet mask," the number of zero/one bits in the address used to number hosts within the prefix.  While we use conventions like the "dotted-quad" scheme aaa.bbb.ccc.ddd, all traditional ("IPv4") addresses are 32-bit binary numbers.  (Next-generation "IPv6" addresses are 64 bits long.)

Some network ranges have been set aside to be used solely for private networks.  Routers typically use one of these networks to assign addresses to hosts on the LAN side.  One commonly-used private network range is 192.168.0.0 through 192.168.255.255.  The most common scheme creates what used to be called a "class-C" network with 24 bits associated with the prefix, and eight bits used to identify individual hosts.  So, for instance, your router might use 192.168.1. as the prefix for all the addresses it assigns, creating a range from 192.168.1.0 through 192.168.1.255.  This network is referred to as 192.168.1.0/24, signifying that it starts with the "network address" 192.168.1.0 and has 24 bits assigned to the network prefix.

---

### Post by vysero on 2018-08-30
So if your address was 10.11.1.0/24 then the /24 part isn't actually part of the address but is indicating how much of the 10.11.1.0 is the network address? So in other words there's no command I would type that would say: LAN: 10.11.1.0/24 it would simply say: inet addr: 10.11.1.0 is that right?

EDIT:

Sorry no I misunderstood. I was looking at address displayed from ifconfig vs ip addr.

---

### Post by The Cog on 2018-08-30
ifconfig shows something like ```
inet 192.168.0.102  netmask 255.255.255.0
``` instead. It's the same info in a different format. The netmask of 255.255.255.0 gives a binary value of 11111111111111111111111100000000 which is 24 ones and 8 zeros. The ones show how much of the whole IP address is network number. I prefer the /24 notation personally.

---

### Post by vysero on 2018-08-30
Alright great thanks guys!!

---

