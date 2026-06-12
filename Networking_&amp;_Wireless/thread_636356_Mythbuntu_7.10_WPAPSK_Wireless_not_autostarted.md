---
title: "Mythbuntu 7.10 WPAPSK Wireless not autostarted"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by WatsonJX on 2007-12-09
Hi there,

I have just installed mythbuntu 7.10. The wireless card is supported by rt61pci and WPAPSK is configured successfully. I want it brought up upon reboot so I removed NetworkManager and related package and WPAPSK settings are added in /etc/network/interfaces. ifup wlan0 can bring it up without problem after I login. But after reboot, it is not automatically started.  Now I added in rc.local the command /etc/init.d/networking restart to make it work.

I googled and early version of wpasupplicant needs af_packet to be loaded first in Ubuntu 6.10. I tried add af_packet in /etc/modules and it still doesn't work.  Don't know what's the reason behind it now.

I have Ubuntu 7.10 on another machine and have not noticed such problem though.

Thanks for any hint.

---

