---
title: "Unstable Bit rate on BCM4318, down to 5Mb/s"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by Xav' on 2007-12-03
I haven't seen this problem reported before (sorry if I have missed a thread about that). I have a Broadcom wireless card with a bcm4318 chipset (apparently a problematic one). I used ndiswrapped and the bcmwl5 driver to get it to work. At first it was great, 54 Mb/s, but as time passes the connection fluctuates and degrades down to 5 Mb/s... a simple restart put it back to 54 then goes down again... Any ideas ? I should mention that the network or AP is not faulty. Here is a copy of iwconfig over time :

xav@xav-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Shuman Lab"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:E3:9B:90:A0
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xav@xav-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Shuman Lab"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:E3:9B:90:A0
          Bit Rate=24 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xav@xav-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Shuman Lab"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:E3:9B:90:A0
          Bit Rate=48 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xav@xav-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Shuman Lab"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:E3:9B:90:A0
          Bit Rate=36 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xav@xav-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Shuman Lab"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:E3:9B:90:A0
          Bit Rate=5.5 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Xav' on 2007-12-26
Well, I finally gave up... I switched to an other wireless card (rt61 chipset), installed windows driver with ndiswrapper and I now have a stable wireless connection.
Still don't know what was wrong with the BCM4318...

---

