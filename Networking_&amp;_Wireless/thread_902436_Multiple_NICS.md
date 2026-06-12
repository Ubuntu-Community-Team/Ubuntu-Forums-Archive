---
title: "Multiple NICS"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by chrissezhi on 2008-08-27
Good day all - 

ok - total newbie here. I have Ubuntu Hardy installed with 3 nics along with VMware Server. I am only dealing with Ubuntu at this time. I have assigned static IP's to each of the network cards. I can see the nics if running ifconfig. If I ping in order say x.x.x.15 x.x.x.16 and x.x.x.17 I get replies. If I unplug one of the cables, I still get replies on all three IP addresses. I will not get a reply if all 3 network cables are disconnected. Please help. I want these to be seperate and not bonded/teamed. Plan is to have one eth to local LAN and the other to a DSL connection. Planning on achieving via VLAN on Cisco Switch. 

Thanks for your help.

Chris

---

### Post by Iowan on 2008-08-27
Just a theory: As long as any interface is active, networking may be "up" and "onboard" addresses may be active.  (I'm a li'l surprised it works with all 3 in same subnet).

---

### Post by SpaceTeddy on 2008-08-27
A Computer cannot have more than one ip in one segment unless you are deliberatily assigning it to virtual devices. You can have multiple NICS in the same physical segment, but they must be in different ip subnets. Ohterwise, the kernel might now know which device to use when - it confuses the network and has no added benefit (for my taste)...

Like i said, if you want the computer to have multiple ip-addresses, use one network card and assign multiple ip-addresses to it. 

hope it helps :)

---

### Post by Iowan on 2008-08-27
Try different subnets for the 3 NIC's and see what happens.

---

