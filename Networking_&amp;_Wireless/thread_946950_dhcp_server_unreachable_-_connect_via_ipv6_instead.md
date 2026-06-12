---
title: "dhcp server unreachable - connect via ipv6 instead?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by skulda on 2008-10-13
Hey!
I'm living in a university housing and there is wireless access but it's very very unstable. A common problem is, that the DHCP (IPv4) server does not respond for hours. But at the same time, people using vista can connect, which is (as you will understand) really annoying me!
I suppose this is due to the fact that vista has ipv6 enabled by default and the use autoconfig and don't need the dhcp server. (Wireshark shows a lot of ipv6 traffic in the air, so I suppose the routers support it...)
Now, I would like to do the same, but I don't get it.
**What do I have to do, to connect via ipv6 to the router?**

I'm running Kubuntu 8.04, the output of iwconfig and ifconfig when connected are posted below:

> iwconfig ath0
ath0      IEEE 802.11g  ESSID:"CROUS-VPN"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:07:8C:48:D0
          Bit Rate:11 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=19/70  Signal level=-77 dBm  Noise level=-96 dBm
          Rx invalid nwid:138812  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:15:af:42:9e:5b
          inet addr:10.9.30.99  Bcast:10.9.31.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:85748348 (81.7 MB)  TX bytes:6279553 (5.9 MB)


I'd be very lucky if you could help me
Thanks in advance
Skulda

---

