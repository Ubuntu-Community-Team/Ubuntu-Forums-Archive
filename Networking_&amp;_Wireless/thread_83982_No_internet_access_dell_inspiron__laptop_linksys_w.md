---
title: "No internet access dell inspiron  laptop linksys wpc54g-v2 pcmcia"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by david1948 on 2005-10-30
Just installed ubuntu 5.04 and i cannot connect to the internet.ubuntu is installed on a dell inspiron 5000E 600 Mhz cpu 256 Mgs of ram. i am using a linksys wpc54g-v2  wireless notebook card take a look at my iwconfig /ifconfig  from konsole.

 root@Eveningstar:/home/gerald # iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"genesis"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@Eveningstar:/home/gerald # ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:192452 (187.9 KiB)  TX bytes:192452 (187.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:DB:BC:74
          inet6 addr: fe80::20f:66ff:fedb:bc74/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

In the network connection properties wlan0 is disconnected sometimes I can see activity Received and sent packet data, but no matter how many times I try to configure wlan0 I always end up with wlan0 disconnected, and sometimes the interface switches back and forth from DHCP and STATIC. there is a  connection icon on the taskbar when selecting properties and choosing lo it is actually sending and receiving data. when selecting Wlan0 the icon show a  triangle yellow icon with a exclamation point.can someone enlighten me on this

---

