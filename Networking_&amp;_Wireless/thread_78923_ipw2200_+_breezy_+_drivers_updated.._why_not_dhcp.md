---
title: "ipw2200 + breezy + drivers updated.. why not dhcp?"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by zinho on 2005-10-19
Hi to all! First, sorry for my bad english..

I've updated my laptop, a samsung x05 to ubuntu breezy. In hoary, through this forum, I could solve the problem with the drivers ipw2200, and all work ok. But in breezy, and after that I've update the drivers and firmware, the wifi don't work.

If I do a "iwconfig" all seems well, but if I do "dhclient eth0", the system cannot receive any ip from the router (I have configured the lan by dhcp).

Why? How can I solve this? If anybody need more information, I can post here.

Thanks!

PD: I haven't wpa, only wep.

---

### Post by Stealth on 2005-10-19
I had this problem to, what you have to do first is tell it to find your gateway. I think you can do this via command line like:

sudo route add default-gateway ip.of.your.router
or sudo route add default ip.of.your.router

Or, like I did since I have a static IP, in /etc/network/interfaces you can add under your main networh device (eth0 I'm guessing) the line:

gateway ip.of.your.router


Then try dhclient! :D

---

