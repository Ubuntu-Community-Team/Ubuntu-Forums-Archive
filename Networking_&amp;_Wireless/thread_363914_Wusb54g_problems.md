---
title: "Wusb54g problems"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by foshizl on 2007-02-17
ive read through countless posts on this forum, and still cant get past the problem I am having... The adapter has installed fine, and shows up as wlan0 in iwconfig and in the network manager, my problem is that i cannot get it to associate with ANY access point, i figured it could be an encryption problem, so i temporarly removed the key from my AP and still it will not connect...

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Smoothwall Box"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:00:00:00:07:BA
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-38 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Floppyjoe on 2007-02-17
It shows here you have two wireless adapters. One for eth1 and one for wlan0.
have your tried:
```
sudo dhclient eth1
```

It looks like the eth1 adapter is associated with a Access point.

---

