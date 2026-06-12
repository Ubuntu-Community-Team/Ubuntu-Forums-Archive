---
title: "Ubuntu 6.06 hangs when loading hardware drivers because of Linksys LNE100TX"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by Enil8 on 2006-07-18
I had Ubuntu installed on an old PC that I had laying around and I wanted to install one of my old Linksys LNE100TX PCI NIC cards in it. After I put it in and tried booting up Ubuntu again, it hangs when trying to load the hardware drivers. What can I do about this? Is there more information needed? Thanks for all your help!

---

### Post by Enil8 on 2006-07-19
Here's some more information I got about it by removing the splash screen. When it gets to this line:
> eth0: ADMtek Comet rev 17 at 0001e000, MAC ADDRESS, IRQ 11.
BUG: soft lockup detected on CPU#0!
Pid: 2859, comm:   modprobe
...
By MAC ADDRESS I mean the MAC of my card that's installed. Does any of this help? Is the rest of the message needed? Info about EIP and the registers and what not?

---

