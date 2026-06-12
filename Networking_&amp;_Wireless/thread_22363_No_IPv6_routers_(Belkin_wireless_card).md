---
title: "No IPv6 routers (Belkin wireless card)"
date: 2005-03-27
forum: Networking &amp; Wireless
---

### Post by Jason-X on 2005-03-27
Hi all,

I'm having a bit of trouble making my "Belkin 54g wireless notebook card(F5D7010uk)" with Ubuntu (Hoary).

I set my laptop up so that the driver loads on boot and the card is activated.
This all went smoothly using ndiswrapper and the driver(RT2500).

This is the output of iwconfig:


wlan0     IEEE 802.11g  ESSID:"essidname"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:xx:xx:xx:xx:xx
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-120 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-41 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Everything seems to be present and correct to me. Am I missing something here? It seems to send data but not recieve.

Here is a small part of my dmesg output:

ndiswrapper: using irq 9
wlan0: ndiswrapper ethernet device 00:xx:xx:xx:xx:xx using driver rt2500
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
wlan0: no IPv6 routers present

Does this mean anything to anybody? What does the bit about "**no IPv6 routers**" mean?

I would love to get my laptop working wirelessly with Ububtu. If anybody can help me it would be much appreciated.

Thanks Jason

---

### Post by Jason-X on 2005-03-28
Anybody ??

---

