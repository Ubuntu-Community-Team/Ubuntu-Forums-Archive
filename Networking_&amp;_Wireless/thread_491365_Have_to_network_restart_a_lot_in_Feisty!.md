---
title: "Have to network restart a lot in Feisty!?"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by tedrogers on 2007-07-03
Hi,

Wondering if anyone knows what's going on here...after following the wireless howto here:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

It worked flawlessly for ages, but when I upgraded from Edgy to Fesity I often have to restart my wireless network manually after booting into X. Sometimes several times to get it to work.

During the boot sequence I can see that the wireless card is trying to bind to my router using DHCP (the restart-networking script is running)..and there is verbose output regarding the attempts to get a DHCP offer.

Sometimes if succeeds and most of the time it fails....so that when I eventually log in I have to manually run /etc/init.d/networking restart in order to get it to connect and bind to my router properly using DHCP.

Any ideas why this is happening and how can I sort it out...it's becoming a pain now.

Thanks.

---

