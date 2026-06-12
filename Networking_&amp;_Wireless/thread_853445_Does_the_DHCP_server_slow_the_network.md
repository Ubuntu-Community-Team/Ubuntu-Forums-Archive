---
title: "Does the DHCP server slow the network?"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by thecobraeffect on 2008-07-08
I'm trying to take care of a network in Iraq, we bought the system from a group before us set it up, but they were not terribly computer savvy. I've got some networking experience, but the network seems to go down (unable to ping the switch, or router, very very slow access to the internet) when a lot of people hop onto the network. It seems like we have intranet issues when a lot of people are using it, which I don't *think* should happen, it's not like we're cramming 50 people through an 8 port router.

Does a DHCP server take up a lot of the routers ability? Will assigning IP addresses speed my network up at all? 

Our set up has a 24 port switch connected to a router, with two 5 port switches on the ends. There are 30 computers connected to the network. Is it just too many people for the equipment we have? The 24 port switch and the router are both net gear, which would not have been my choice, but they should be good enough, right?

Thanks!

---

### Post by Paul Weaver on 2008-07-08
> **thecobraeffect said:**
> I'm trying to take care of a network in Iraq, we bought the system from a group before us set it up, but they were not terribly computer savvy. I've got some networking experience, but the network seems to go down (unable to ping the switch, or router, very very slow access to the internet) when a lot of people hop onto the network. It seems like we have intranet issues when a lot of people are using it, which I don't *think* should happen, it's not like we're cramming 50 people through an 8 port router.


I'd concentrate on the local network first, I'm guessing external connectivity in Iraq is flaky at best. When the router goes down can you still ping other machiens on the local network (implying a layer 3 software issue)

> 
Does a DHCP server take up a lot of the routers ability? Will assigning IP addresses speed my network up at all? 


No, not unless it's a really awful dhcp server -- you could disable it on the router and run one on a linux box on the network if you really wanted to be sure. 

> Our set up has a 24 port switch connected to a router, with two 5 port switches on the ends. There are 30 computers connected to the network. Is it just too many people for the equipment we have? The 24 port switch and the router are both net gear, which would not have been my choice, but they should be good enough, right?

Thanks!

Should be fine. First rule is to simplify things, can you ping a machine on same switch, on a different switch, ping the router, etc. Unplug everything but two machines and a single switch, rule it out. Add the others, rule it out. Add the router. Etc. 

Sounds to me that it's a dodgy router, perhaps try swapping it out (depending on your upstream connection -- ethernet, adsl, isdn etc, you could use a linux box with 2 nics)

---

### Post by thecobraeffect on 2008-07-09
I think it is a router problem as well, the router they have is a netgear FVG318, which is an 8 port switch as well as a wireless router. There are no wires running into the router, and the wireless is disabled. It only seems to like giving out 13 IP addresses at a time, which leads to our vista users (and those on the 5 port switches) using each-other as proxies and creating loops. 

The firmware is out of date, I'm going to give downloading it and updating it and the switch a try today, but it's hard to test the equipment because everyone always wants to get on the internet.

When the network goes down, I can watch my ping time to the switch increase, and eventually it won't return anything. After that, I start to lose the switch, and but I can always ping other computers within this switch. I didn't try pinging the other switches, yet. A layer 3 software issue would be the router, correct? I know they are sometimes called layer 3 switches, but I'm not sure. Unfortunately, I don't have two ethernet ports on my laptop here, but I can try to have another one sent over to use as a router.

If I did that, I would have a lot more control of the network, and be able to watch the problem a lot more effectively, correct?

Thanks again for all your help.

---

### Post by Paul Weaver on 2008-07-15
Yes, it's most likely the routing software in the router/switch. The swithcing (passing packets from one PC to another) is likely done nearer the hardware. Layer 3 switches are something a little different, you are unlikely to have one.

If you did have a PC with two network cards, you could use that as a router. You plug one side into a switch, and the other side into the internet. It depends on how your internet arrives in the building, it would need to be ethernet, or a supported USB device. If you did use a PC to do your routing you could run wireshark on it, and see all the packets coming in and going out, and even keep track of who uses the most bandwidth.

If you have problems with DHCP, I'd adivse you look at setting up static addresses for all your client pcs. As long as they dont change very often and you've got less than 50 you should be fine, just keep a track of which ones you've assigned.

---

