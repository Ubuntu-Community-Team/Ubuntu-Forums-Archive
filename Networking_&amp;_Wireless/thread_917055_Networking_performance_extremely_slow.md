---
title: "Networking performance extremely slow"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Vadi on 2008-09-11
Hi,

I have an odd issue. Wireless on my laptop on my home network is fine - it's very quick and does encryption fine.

However, it is *excruciatingly* slow on my university network. So slow that sometimes I can't even login (I do it via a web page). Other laptops work fine, even ones with Ubuntu. Network Manager shows 3-4 bars in the icon also.

This also happens randomly. Sometimes it's fine, sometimes it's not. Right now it's not fine.

Can anyone help?

Here's the output of iwconfig:

> $ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"AirYork"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:02:8A:9E:4F:2F   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=64/100  Signal level=-67 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



---

