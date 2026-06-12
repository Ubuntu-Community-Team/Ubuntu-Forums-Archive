---
title: "Wireless problem: Can see, cannot connect"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by zumbi77 on 2007-10-29
Using 7.10 I can see different wireless networks, even more than when using XP. Unfortunately I can't connect to any of the networks I see. I've tried using both network-manager and wicd.

It's a Broadcom 4306 card.

iwconfig reads:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ddrichardson on 2007-10-29
It could be a driver issue, have you tried using ndiswrapper with known good xp drivers?

---

