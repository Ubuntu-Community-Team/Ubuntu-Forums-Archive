---
title: "Feisty Wireless Problem"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Boule on 2007-04-20
Hi,

I installed feisty on a laptop that doesn't have an integrated wireless card. I had a linksys wireless-g adapter (pcmcia) plugged in during the install. Now that the install is complete, I'm unable to connect to any wireless network. When I click on the NetworkMAnager icon, I don't see any network available. I also checked in the drivers section, there is only nvidia.

I typed iwconfig, and here's the output:```

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I also tried a manual configuration with my access point settings, it didn't work...

Any ideas ?

Thanks !

---

### Post by zPacKRat on 2007-04-20
use synaptic and install bcm43xx-firmwarecutter and it will extract what it needs from your wireless card and you should be good to go.

---

### Post by Boule on 2007-04-20
Thx, it worked like a charm :)

---

