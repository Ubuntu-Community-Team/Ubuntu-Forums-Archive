---
title: "NIC problems! (SMC1233A-TX and D-Link DE-528)"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by Calmatory on 2008-03-06
New motherboard, no integrated NIC, thus I need to use PCI NIC. I got two of them. Not either of them work. D-Link DE-528 reports the same as [this](http://ubuntuforums.org/showthread.php?t=67258) thread, no-go.

As for the SMC1233A-TX, it seems to be using ADMtek's AN983B-chip. Nothing else I know about it, except that it doesn't work. I haven't done any deep investiagion with it really.

What can I do? Use Windows? Return to the old machine? Get new NIC?

Oh, btw, PuppyLinux seems to be getting that SMC1233A-TX working IIRC. With it's Network Wizzard or something alike.


Edit: BOTH cards work flawlessly with Puppy when used Puppy's Configuration wizzard. What it seems to be doing is to load ne2k-pci module and then look for "alive networks"(How??) and then query DHCP with(?) dhcdp(?). I don't know why it doesn't work in the first place, since the only thing it seems to be doing(at least the only thing I am told it does) is to query the DHCP server. How can I do this manually? Actually the ne2k-pci module is already loaded upon boot AFAIK. And so is DHCP queried aswell, AFAIK. But why on earth doesn't it work in the first place without the wizzard?

EDIT: ```
ifup eth1
``` was the solution! :)

---

