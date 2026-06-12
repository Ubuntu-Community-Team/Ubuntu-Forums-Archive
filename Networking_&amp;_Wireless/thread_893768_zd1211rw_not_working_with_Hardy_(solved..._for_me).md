---
title: "zd1211rw not working with Hardy (solved... for me)"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by mhxj on 2008-08-18
I have a ZyDAS WLAN WL400 (0ACE:1211) directly connected to the mainboard. Hardy with kernel 2.6.24-19.generic AMD64. Upon connection of the stick, CPU utilization raises up to nearly 100%. top indicates that ksoftirqd is eating all the CPU cycles.

Needless to say that WLAN is not working :-)

I read somewhere of people having the same trouble which were stating that the same hardware worked with Gutsy. I installed the kernel of Gutsy and in fact my WLAN then was working.

To make it work with the Hardy kernel, I installed the kernel sources of the running kernel and the sources of the Gutsy kernel. Then I copied the zd1211rw sources from the old kernel to the new one and compiled it (no need to install the new kernel neither to build a package).

In fact, the old files do not compile in the new tree, because of 2 missing macros. I had to extract them from /usr/src/linux-2.6.22/include/linux/netdevice.h (Gutsy) and paste them into /usr/src/linux-2.6.24/drivers/net/wireless/zd1211rw/zd_netdev.h (Hardy)

At the end I got a new zd1211rw.ko which replaces the original one in /lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/zd1211rw/

Of course this recipe is just a guideline and it is missing a lot of intermediate steps. For those of you using the 2.6.24-19-generic X86_64 kernel, you can download the kernel module from here:

[http://web3.h5885.serverkompetenz.net/zd1211rw/](http://web3.h5885.serverkompetenz.net/zd1211rw/)

Good luck!

---

