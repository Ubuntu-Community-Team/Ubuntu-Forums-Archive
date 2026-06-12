---
title: "`NAT': Table does not exist"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by abhs-94 on 2015-05-06
Hi all
I am trying to run hostapd based wireless hotspot from my linux laptop. I have been using this particular scheme since the past 3 years that I have owned this machine. However, after a recent re-installation of Ubuntu 14.04, I found this error cropping up when I try to add iptable rules for redirection:

> iptables v1.4.21: can't initialize iptables table `NAT': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

I have tried to modprobe the module iptable_nat  and that hasn't resolved the issue either.

It seems to me that kernel 3.13 aimed to replace iptables with something called nftables. Is it the case that ubuntu is amidst that transition but hasn't completed it?


Any help is apprecitated

Thanks a lot!

---

### Post by The Cog on 2015-05-06
Table nat does exist in 14.04 (and 14.10 and 15.04). It is there by default. But it is "nat", not "NAT". Lower case for that table name is important.

---

### Post by abhs-94 on 2015-05-07
Thank you
That helped!

---

