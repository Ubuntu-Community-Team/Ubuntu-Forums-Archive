---
title: "Wireless Disconnects Automatically..."
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by Helix_Spear on 2007-06-24
Hi Guy,

Today i encountered this problem of having my wireless getting disconnected automatically while working on Ubuntu 7.04...
and i cant join back i have restart my laptop in order to join back...
did any of you faced this problem... Help is needed... i tried both WICD and network-manager-gnome...
same problem

thank you guys.

Hamja

---

### Post by saucerboy on 2007-12-21
I'm having the same issue in 7.10. The other machines connected to the same access point are unaffected. Restarting the machine brings the connection back.

Any suggestions?

Thanks.

---

### Post by Gigamo on 2008-01-26
I'm having the same issue. At a random time (can be a day, can be 2 hours uptime) my WICD will drop its internet connection and I cannot reconnect at all (the program crashes). The only solution is rebooting, and this is extremely annoying.

---

### Post by DO55 on 2008-01-26
same problem 
windows dose not have this problem

---

### Post by Gigamo on 2008-01-26
I have just upgraded my wicd from 1.3.1 (the one in the repository) to 1.4.1, and I will report back if this fixes the issue.

---

### Post by gmatt on 2008-02-05
Hi,

Without too much indepth analysis I recommend that you try to turn of IPv6. It seems to be wreaking havoc across wireless networks across the globe.

- edit /etc/modprobe.d/aliases
- change line "alias net-pf-10 ipv6" to "alias net-pf-10 off ipv6"
- reboot

source:[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/158481](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/158481)

This has seemed to worked for me and I've been having this same problem. I haven't had a wireless disconnect since my last reboot. Usually I would get a disconnect every 30min-1hr or so and I could only reset it by rebooting. It probably isn't the fault of the software; I imagine its the routers that do not yet support IPv6.

a quick skim of this article by microsoft (yes I know, I feel like I'm somehow violating something very sacred by linking to microsoft in the ubuntu forums) describes problems with routers and IPv6:

[http://www.microsoft.com/whdc/device/network/IPv6_IGD.mspx](http://www.microsoft.com/whdc/device/network/IPv6_IGD.mspx)

PS I didn't read that microsoft article just skimmed it and it seemed to "encourge" router manufacturers to implement IPv6 native support in routers, which seems to imply that they currently don't support it

good luck!

---

