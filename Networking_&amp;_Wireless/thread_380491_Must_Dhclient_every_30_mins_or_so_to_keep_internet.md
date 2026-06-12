---
title: "Must Dhclient every 30 mins or so to keep internet working"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by matkline on 2007-03-09
Hey all,

Any suggestion as to how to get it so I don't have to run dhclient all the time?

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"UNC-1"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:24:F4:B2:50
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig: 

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:81:84:D3
          inet addr:152.23.80.163  Bcast:152.23.87.255  Mask:255.255.248.0
          inet6 addr: fe80::216:ceff:fe81:84d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64658951 (61.6 MiB)  TX bytes:4479752 (4.2 MiB)
          Interrupt:66 Memory:edf00000-edf10000

I just got my wireless working a few hours ago for the first time, so I'm kinda wary of a reboot.

I'm running Dapper Drake, 2.6.15-26-386

---

