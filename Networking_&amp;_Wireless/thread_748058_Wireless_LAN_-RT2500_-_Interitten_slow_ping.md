---
title: "Wireless LAN -RT2500 - Interitten slow ping"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by rtmie on 2008-04-07
I am having a strange problem with Gutsy (AMD64Bit) with intermittent slow pings to the wireless router from my desktop PC (laptop with Intel Corporation PRO/Wireless 2915ABG, does not show same problem).

My assumption is that this is either config or driver issue on this box. Anyone encountered similar or have solution?

Thanks

Rob

===============Details follow =================================

Network Card:  Belkin F5D7000 Wireless G Desktop Network Card
Chipset:  RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
OS: Ubuntu 7.10 (x86_64)
Kernel: 2.6.22-14-generic
Wirelesss Config: WPA security
Wireless Router: Netgear DG834GT

IWconfig
-----------

wlan0     RT2500 Wireless  ESSID:"XXXXX"
          Mode:Managed  Frequency=2.432 GHz  Access Point: XX:XX:XX:XX:XX:XX
          Bit Rate=54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-52 dBm  Noise level:-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Output from ping to router:

 64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.09 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.03 ms
[B]64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1069 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=70.1 ms[/B]
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.18 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=1.05 ms
[B]64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=1041 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=41.9 ms[/B]
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=1.01 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=1.02 ms
[B]64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=1037 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=38.1 ms[/B]
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=1.04 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=1.03 ms
[B]64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=1033 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=33.8 ms[/B]
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=1.19 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=1.12 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=1.18 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=64 time=1.15 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=64 time=1.22 ms
[B]64 bytes from 192.168.1.1: icmp_seq=35 ttl=64 time=1029 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=64 time=29.8 ms[/B]
64 bytes from 192.168.1.1: icmp_seq=37 ttl=64 time=1.45 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=39 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=64 time=1.04 ms

---

### Post by rtmie on 2008-04-11
Ok, got a solution. Problem seems to have been with rt2500 module. Downloaded newest cvs daily tar ball from serialmonkey and installed. Problem seems now to be gone

Rob

---

