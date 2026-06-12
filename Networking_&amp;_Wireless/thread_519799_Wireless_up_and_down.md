---
title: "Wireless up and down"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by atomic_turtle on 2007-08-07
Hi,

I thought it should be fairly simple to activate and deactivate a wireless interface. "sudo ifconfig athx up" and "sudo ifconfig athx down" respectively (given the entry in the /etc/network/interfaces that is the wireless connection). On my little subnotebook I'm naturally trying to max out my battery by deactivating and then physically removing the wireless card whenever it's not needed. So I have two aliases, "net" for activating the interface with the command above and "nonet" for deactivating it in addition to pulling out the card. But apparently, it doesn't work. Once I've removed the wireless card, e.g. after downloading all my emails with thunderbird, I can't activate it again: When I try (to send my answers), it doesn't work and when I open Firefox, I get errors loading pages. When I do a network restart (sudo /etc/init.d/networking restart), everything is fine.
Can anybody tell me what I have been doing wrong?
Thanks a lot!
Regards,

atomic_turtle

---

### Post by spd106 on 2007-08-07
I suggest you look into using the ifup and ifdown scripts instead. AFAIK they were designed for this purpose.

---

