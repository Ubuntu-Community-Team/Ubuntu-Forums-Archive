---
title: "Cant start my wireless card in monitor mode"
date: 2018-06-13
forum: Networking &amp; Wireless
---

### Post by aayush1998 on 2018-06-13
hi
using ubuntu 18.04
i am trying aircrack-ng
i came up on a problem i cant start my wireless card in monitor mode i tried iwconfig and ifconfig wlan0 down giving a error pls help
belphegor@Lucifer:~$ iwconfig
lo        no wireless extensions.

enp7s0    no wireless extensions.

wlp6s0    IEEE 802.11  ESSID:"Seven Deadly Sins"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 38:E6:0A:C5:D6:F2   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

belphegor@Lucifer:~$ ifconfig wlp6s0 down
SIOCSIFFLAGS: Operation not permitted

---

### Post by QIII on 2018-06-13
We do not allow discussions about aircrack-ng.

Closed.

---

