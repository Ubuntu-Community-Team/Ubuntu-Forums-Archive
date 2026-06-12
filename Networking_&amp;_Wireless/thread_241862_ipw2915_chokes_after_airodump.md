---
title: "ipw2915 chokes after airodump"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by bull8042 on 2006-08-22
I have a Dell 9100 with an Intel 2915 wireless card. I am running Dapper in the KDE flavor and using network-manager for my wireless configuration because I chose to use WPA on my home network.
The problem I am having is after running Kismet and then Airodump for a while, I can no longer connect to any wireless networks without fiddling with the eth1 configuration. It won't come back even after rebooting. The last time I ran Airodump for several hours, I ended up re-installing Dapper to get my wireless back. I first tried uninstalling all of my network "stuff" (ie - Ethereal, Karpski, Knmap, Wireless Assistant, etc), then reinstalling network-manager. But nothing worked. Any ideas?....
Thanks,
Bull

---

### Post by spd106 on 2006-08-23
Airodump requires that the interface is set to monitor mode. So to enable you to connect to an AP it must be set back to master/infrastructure mode.

If that is no use why not use a live CD such as BackTrack ( aka Auditor) for  network monitoring, then reboot back to Ubuntu.

---

### Post by bull8042 on 2006-08-23
> **spd106 said:**
> Airodump requires that the interface is set to monitor mode. So to enable you to connect to an AP it must be set back to master/infrastructure mode.

If that is no use why not use a live CD such as BackTrack ( aka Auditor) for  network monitoring, then reboot back to Ubuntu.

I thought about it being stuck in monitor mode, but I hadn't figured out how to get it back. I switched to Ubuntu back in Oct, but I haven't yet learned about all of the CLI goodies.
I have diddled with BackTrack a bit. There are a lot of really nice tools there, but if memory serves me correctly, I had trouble getting Airodump to work. I will give it another shot though.
Thanks for your help.

---

