---
title: "Wireless point-to-point"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by mrsva on 2005-09-14
Hi all!

I have at home a notebook which has a wireless card (on board) and a desktop connected to a DSL line.

The desktop doesn't have any wireless connectivity (only bluetooh via an USB adapter). 

I was thinking of connectiong the two of them using a wireless network but before I buy any card (or USB adapter) I would like to know if it is possible to connect them directly, without any router.

I am asking this bacause in a normal cable network, with normal cables, one need to have a hub ou use a crossover cable. 

So I was wandering if the direct connection with the wireless adapter will work.

I am planning to buy this USB adapters that look like a memory stick. I see from the [ HOWTO: WLan via Ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=31926&highlight=wireless+point) that it is possible to make this cards to work with linux.

By the way, anyone have tried to connect 2 computers using bluetooth? Does it works?

Thanks!

Marcio

---

### Post by mlomker on 2005-09-15
How is the PC connected to the Internet?  A USB connection or through an ethernet cable to a dsl modem?

To answer your question it is technically possible to do what you're describing.  It is also quite difficult if you aren't experience in operating systems and networking.  It'd be much easier to connect both machines to your Internet connection directly.

---

### Post by mrsva on 2005-09-15
[QUOTE=mlomker]How is the PC connected to the Internet?  A USB connection or through an ethernet cable to a dsl modem?[/QUOTE]

ethernet cable to a dsl modem

> To answer your question it is technically possible to do what you're describing.  It is also quite difficult if you aren't experience in operating systems and networking.

Actually, the connection is already working with a crossover cable. The desktop is routing the trafic from/to the notebook and it is running a firewall. I think that after having the wireless card working on the desktop, it should be easy to configure (in a similar way) to use the wireless connection. I was not sure if this was possible with wireless to connect directly without the hub because with cable I need a special cable  (crossover) if I don't want to have the hub.

> It'd be much easier to connect both machines to your Internet connection directly.

But then I need to buy a wireless hub, which will be more expensive then the USB adapter.  ;-) 

Thanks,

Marcio

---

### Post by mlomker on 2005-09-16
[QUOTE=mrsva]But then I need to buy a wireless hub, which will be more expensive then the USB adapter.  ;-)[/QUOTE]

Not from what I've seen.  Best Buy has them down to about $40 and the 802.11b-only ones are almost free on E-bay.

Wireless will work fine between two machines.  You just have to configure the connection for 'ad-hoc' mode rather than 'managed'.

---

### Post by mrsva on 2005-09-23
[QUOTE=mlomker]Not from what I've seen.  Best Buy has them down to about $40 and the 802.11b-only ones are almost free on E-bay.[/QUOTE]

thanks for the tip. I bought a wireless router (D-Link DI-624+ 54). It was not as expensive as I thought! :-) And it has lots of nice features:

[LIST]
[*] now I can use my notebook or my desktop with my DSL connection independently (with the p2p approach, I would need to turn on the desktop allways as it would manage the DSL modem). This router can connect directly to the modem and has a built-in dhcp server to give addresses to other computers

[*] I thought I would not be able to connect to my desktop from outside (using ssh or http) because of the router, but it has a built-in firewall and is possible to do port forwarding in a very ease way.

[*] it has also a built-in client for dyndns.org, so I can keep the name for my machine (I was really not expecting something like that!)
[/LIST]

I wasn't expecting so much features in this kind of device! Thanks again for the tip!

Marcio

---

