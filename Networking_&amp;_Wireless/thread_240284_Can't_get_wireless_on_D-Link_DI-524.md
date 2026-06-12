---
title: "Can't get wireless on D-Link DI-524"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by ktm5124 on 2006-08-20
So we have a 802.11g wireless signal on a D-Link DI-524 router which is WEPped. Weirdly enough, I can get wireless working at my friend's house on linux, in which the wireless is also WEPped. I can't get wireless working at home on linux, though, and I can get wireless working on Windows at home. So it can't be a MAC address thing.

My eth1 wireless connection is active and enabled. When I check its status, however, it says it's disconnected. And of course it doesn't work when I try it. Anyone have any ideas what I have to do to get it working?

Here is the output for iwconfig:

lo        no wireless extensions.

eth1      unassociated  ESSID:"Evergreen"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by thomasaaron on 2008-07-10
Did you ever get wirelss working on the wep'd dlink 524? If so, how?

---

