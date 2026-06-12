---
title: "Only One Eth Interface Is Brought Up At Live CD Boot"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by tCarls on 2007-12-10
I'm booting a board with six ethernet ports to a live Feisty CD. When its done booting only eth5 has an IP address. I have to run dhclient to assign IP addresses to the other ports. I need all interfaces to come up automatically at boot. I'm thinking about remastering the CD and adding dhclient to init.d. Will this work? Is there a better way? Is there a reason that Ubuntu only brings up one interface (probably to save boot time?)

thanks

---

### Post by kevdog on 2007-12-10
6 ethernet ports?? All on different subnets?? Just wondering

---

### Post by tCarls on 2007-12-10
It's a server blade. All the ports are going to one host and are on the same subnet. I know it's an odd situation. I'm writing a functional test for it, which is why I need them to come up automatically. I can't have the operator open a terminal and type dhclient for every board they test.

---

