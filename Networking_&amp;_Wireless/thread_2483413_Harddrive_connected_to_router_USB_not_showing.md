---
title: "Harddrive connected to router USB not showing"
date: 2023-01-29
forum: Networking &amp; Wireless
---

### Post by cmacc77 on 2023-01-29
I have a WD 3 TB my book connected to a sagecom F5380 modem provided by the ISP, and the only place the HD shows is in the routers setup utility.   I would like to use the HD as a media server and as a drive.

It doesn't show up as a media sever on my TV or on any PCs connected to the LAN.  I've tried 2 different HDs and a flash drive connected to 2 different routers, and they never show up on the TV, ubuntu or windows machines.  I've tried every format for the HDs with no luck.

Can anyone advise how to map this as a network drive and access it as a media server?
[[h=3][/h]]("https://manuals.plus/sagemcom/f5380-cooper-wireless-router-manual")

---

### Post by TheFu on 2023-01-30
Never heard of that router.

Be very careful connecting any storage to a router that is also your WAN router. This is because every router that has done that previously had a bug that shared all the storage over the internet.  It is a common problem.  Of course, if you intend to share everything on the storage on the internet, it is a great solution.
This is one of those "features" that is common to routers, but really shouldn't be used.  Of course, if you setup this router NOT to be your WAN router and use it inside your home LAN only, then the risks are mitigated (usually).  However, some storage options on routers will connect to an internet service, keeping a socket open so systems outside can access the storage.  Those have had bugs too, allowing anyone in the world access.

Routers have complex software running on them and bugs are constantly being found.  This is why I only use my router for the standard router things.  Gateway, firewall.  Never storage.  Never a VPN (client or server).  I don't even like to use routers for DHCP/DNS caching, since there have been DHCP attacks which allowed external attackers onto the LAN like our internal LAN devices.

Definitely avoid using NetUSB.  That's the USB storage sharing stuff. 

[https://routersecurity.org/bugs.php](https://routersecurity.org/bugs.php) is a DB of known bugs in routers over the decades.
[https://threatpost.com/asus-home-router-bugs-snooping-attacks/157682/](https://threatpost.com/asus-home-router-bugs-snooping-attacks/157682/)

Anyway, google finds the manual for this router easily, if you still want to see what and how to setup this stuff.  I visited the support website and was not impressed.

---

