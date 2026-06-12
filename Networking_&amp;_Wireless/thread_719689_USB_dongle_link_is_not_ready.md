---
title: "USB dongle: link is not ready"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by insomniux on 2008-03-09
Hi,
I have a working Wifi which I use daily with my laptop (ubuntu 7.04). Now I installed a new desktop (ubuntu 7.10 (64)) and I try to connect with the network. I've tried 2 different USB dongles (Netgear wg111v2 and Zydas 1211). Both detect several wifi networks (output of iwlist), but still I cannot connect. /etc/network/interfaces is the same as on my laptop.

/var/log messages shows repeatedly:
(for the netgear dongle)
Mar  9 18:52:33 desktop kernel: [  256.599922] ADDRCONF(NETDEV_UP): wlan0: link is not ready

(for the zydas dongle)
Mar  9 18:52:33 desktop kernel: [  256.599922] ADDRCONF(NETDEV_UP): eth1: link is not ready

I'm stuck:confused:. Althoug the dongles seem to be communicating (they show the settings of my router), they are not able to connect.

Can someone please help me solve this problem?
Thanks
Mike

---

