---
title: "Cant connect to wlan0"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2006-09-14
For some reason, I can not get the wireless card to start?!

carlo@Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sp0nge on 2006-09-14
Well a little patience and some thought, I discovered that wlan0 was not keeping the ESSID in it's properties... a few config changes later and Po0f, I'm wireless again. If anyone has an idea what I need to do to make this a constant, I'd appreciate not having to re-enter this info on each start up.

---

