---
title: "realtek 8139 problems - same but slightly different"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by cokehabit on 2007-12-10
I have the RTL-8139/8139C/8139C+ Realtek card.

When I turn the computer on I get the network for a while but then it turns off. dhclient eth0 says the network is unreachable.

Ok, I then went a searching for answers and found a multitude of them, mostly the fact that it loads two modules - the 8139cp and the 8139too ones - which mine does.

When I rmmod the 8139too module and start eth0/networking just with the 8132cp then i get ```
cannot find device...
<snip>
Failed to bring up eth0
``` which is very strange...

In fact it wont even see eth0 at all if 8139too isn't there but I need 8139 removed to be able to communicate with the network.

I gave this a try from another thread:```
ifdown eth0
rmmod 8139too
modprobe 8139cp
insmod 8139cp
ifup eth0
```but insmod says "can't read 8139cp: No such file or directory" which is also what it says if i try it with the 8139too module.

I have seen troubles on here with window's wake-On-Lan but this is a pure ubuntu box but it did previously have XP on it though and because it obtains it's network information and starts working again after boot and removal of the network cable I think it may be connected to that.

Also, /etc/hotplug/blacklist has the 8139too driver in it but it still loads it.

Any ideas?

---

### Post by cokehabit on 2007-12-10
No help whatsoever?

I've tried all the answers on the forum

---

