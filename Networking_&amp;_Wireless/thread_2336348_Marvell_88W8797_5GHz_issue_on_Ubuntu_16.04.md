---
title: "Marvell 88W8797 5GHz issue on Ubuntu 16.04"
date: 2016-09-06
forum: Networking &amp; Wireless
---

### Post by davidkisvari on 2016-09-06
Hi!

I have a Surface Pro 2, it has a Marvell 88W8797 wlan controller (USB). It can handle both 2.4 and 5GHz, 2.4 works as intended, but 5GHz doesn't :( Problem is that although I can connect to 5G network, it is way too slow, only a few kB/s can be transferred. iwconfig says the connection speed is 300Mb/s but the actual speed is only a few kBs/s, a simple webpage loads for 10s of seconds.  Router is a TP-Link Archer C5, it's dual band, my internet connection is 120/10 Mb/s. Every device (phones, Windows PC) works well on 5GHz, so it's not the routers fault. 

iwconfig outputs:

2.4GHz:

lo no wireless extensions.


enx281878b7edce no wireless extensions.


wlx501ac50ccee8 IEEE 802.11abgn ESSID:"TP-LINK_8C2E"
Mode:Managed Frequency:2.462 GHz Access Point: E8:DE:27:F8:8C:2E
Bit Rate=144.4 Mb/s
Retry short limit:9 RTS thr=2347 B Fragment thr=2346 B
Power Management:on
Link Quality=63/70 Signal level=-47 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

5GHz:

lo no wireless extensions.


enx281878b7edce no wireless extensions.


wlx501ac50ccee8 IEEE 802.11abgn ESSID:"TP-LINK_8C2D_5G"
Mode:Managed Frequency:5.18 GHz Access Point: E8:DE:27:F8:8C:2D
Bit Rate=300 Mb/s
Retry short limit:9 RTS thr=2347 B Fragment thr=2346 B
Power Management:on
Link Quality=54/70 Signal level=-56 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I have tried every possible configuration of the router, didn't help. Also tried to update to newer firware (linux_firmware_1.160_all (yakkety)), it did help, after reboot 5G was fast as it should be, but the next reboot it was all gone, don't know why. Since then I've tried various firmware versions, didn't help. It should be firmware related, but I don't know what to do next.

Thanks in advance!

David

---

