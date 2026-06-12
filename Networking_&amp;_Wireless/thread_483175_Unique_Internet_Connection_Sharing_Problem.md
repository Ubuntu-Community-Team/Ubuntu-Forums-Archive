---
title: "Unique Internet Connection Sharing Problem"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by ZeroVerteX on 2007-06-24
Hi all!
   Here's my senario. I have a cable modem, Linksys Router, and Linksys access point in my living room. I have my laptop and misc. other computers that I fix for other people in my bedroom. I would like to plug the eth port of my laptop into a switch and plug the other misc computers up to access the internet. I don't mind running DHCP Server on my laptop but if possible I'd like to just allow the misc PCs to get their IP from my router instead of my laptop, basically making my laptop just sort of dumb wireless router. Some people like a diagram, so I'll try to diagram it.

Currently I have...

   [Cable Modem]----[Router]---[AP])))((([Ubuntu Laptop]      [Misc PCs]

I would like to have....

   [Cable Modem]----[Router]---[AP])))((([Ubuntu Laptop]----[Misc PCs]

Any ideas? Thanks all!

---

### Post by kidders on 2007-06-25
Hi there,

You're wordy description made more sense to me than the ASCII diagram ... I wonder if there's a psychological lesson in that hehe. :-k

Depending on how much you know about networking, considering everything within one hop of your laptop's wireless interface, and everything within one hop of its wired interface to be two different networks would probably be the most straightforward thing to do. Consider, for example...[LIST]
[*]**Wireless interface (eg eth0):** 192.168.1.1/255.255.255.0, acquires address by DHCP from your Linksys hardware.
[*]**Wired interface (eg eth1):** 10.0.0.1/255.0.0.0, statically assigned IP, dispenses addresses using a local DHCP server.[/LIST]Your laptop would route between the two LANs, mimicking the sort of thing your DSL modem probably does with your ISP. Of course, depending on how you look at it, having your "misc" PCs in their own subnet could be an advantage or a disadvantage, but since it's a design that follows naturally from the physical layout, it would be easier to set up & manage than the alternatives, imo.

If you have your heart set on running only one DHCP server on your network (and given that it obviously can't be on a laptop), the next most natural solution might be to use your laptop to bridge the two networks.

---

