---
title: "Please help - I can't get wireless working in Edgy"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by kpagpa on 2007-03-17
Hi friends,

I'm struggling to get wireless working in Edgy Eft.

I previously had Dapper, and managed to get it working in that just fine using this guide:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

That isn't working for me now.  I thought it would simply be a case of repeating the instructions, but it isn't working.   I can't even connect on unencrypted, much less WPA which I normally use.

I haven't got Network Manager (why, oh why don't they supply it as part of the basic download?) .  I downloaded the tarball from a website and tried to install it, but it won't even get past ./configure.  It won't compile for some reason.

Can someone please help?

Thanks for your attention!

---

### Post by ingo on 2007-03-18
Try knetworkmanager - a nice little programme that does more or less everything for you (if your wireless card is recognised). > sudo apt-get install knetworkmanager

---

### Post by kpagpa on 2007-03-18
thanks for the tip, I managed to download network manager and it's all looking a lot better:)

---

