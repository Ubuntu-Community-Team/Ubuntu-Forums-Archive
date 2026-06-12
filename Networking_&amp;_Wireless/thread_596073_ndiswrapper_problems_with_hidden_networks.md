---
title: "ndiswrapper problems with hidden networks"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by Cenotaph on 2007-10-29
Hi, 

I'm trying to connect to my Campus network (eduroam) with my BCM4318 card using the ndiswrapper driver and the Network Manager.

I'm setting the network correctly cause i could connect using the bcm43xx driver, but it is too unstable to be a option, can't stay connected for more than a few seconds in most areas.

I remember when i used wpa_supplicant i had to set ap_scan to 2 in wpa_supplicant.conf, or else ndiswrapper wouldn't connect, while the bcm43xx would with ap_scan=1. So, im thinking if the problem could be similar with Network Manager? Is there anyway to solve this?

Thank you.

---

### Post by staticsage on 2007-10-29
The problem you described with ap_scan is indeed the problem you are hitting with NetworkManager:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214)

Towards the bottom of that thread someone wrote a patch for it. It's seems like the ap_scan requirements may differ per chipset. I'm not sure if they are doing anything with this bug, but read there for more details. Perhaps you should contribute to the bug with your exact setup and issue. Hopefully they will fix it...

---

### Post by Cenotaph on 2007-10-29
thanks for the info, unfortunately the mentioned patch didn't seem to do the trick for me. But i'll be checking that bug, then.

---

### Post by Cenotaph on 2007-11-11
ok, as it turns out, not only the Network Manager is the problem. I can't connect at all to an hidden network with ndiswrapper

i uninstalled NetworkManager and im trying to use command line tools only, and putting ap_scan=2 in the wpa_supplicant conf file doesnt work, as it used to work in feisty, i've tested this at home too, so it's confirmed.

Unfortunately, there is no way my univ network will start to get broadcasted in the near future so i really need a way around this without downgrading to feisty.

Any suggestions are appreciated, thank you.

---

