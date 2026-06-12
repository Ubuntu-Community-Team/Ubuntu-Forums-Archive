---
title: "dhcp can't obtain an ip"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by dev.urandom on 2008-11-15
I have a very strange problem here. For some reason, dhclient is not able to obtain an IP from the wireless network here. Due to this problem, both network-manager and wicd cannot obtain IPs automatically, so I have to set them up by hand. On the other hand, Vista manages to obtain an IP just fine, and is able to do it quite fast too. 

On what is probably a related problem, the reported signal strength under Ubuntu is on average 50%, with a minimum of 5% and at maximum 80%. It seems to vary quite often, and sometimes the active connections get reset, or firefox is stuck on the 'waiting' when trying to load a website. These problems do not exist in Vista at all. The signal strength is always reported as 'excellent', and the connection is stable.

This is with an Intel 4965 wireless card (iwlagn module).
2.6.27-8-generic kernel
And I have installed the generic modules backports package.

---

