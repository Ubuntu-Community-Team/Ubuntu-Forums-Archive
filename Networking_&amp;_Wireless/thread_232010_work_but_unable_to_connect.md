---
title: "work but unable to connect"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by 5n1p3r on 2006-08-08
i got a problem with my WI-FI i use Xubuntu 6.06, my WI-FI work but unable to connect to AP, this a message from my /var/log/messages

> 
Aug 9 15:06:58 localhost kernel: [4294679.699000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno>
Aug 9 15:06:58 localhost kernel: [4294679.791000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.3m
Aug 9 15:06:58 localhost kernel: [4294679.791000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Aug 9 15:06:58 localhost kernel: [4294679.791000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection


from that message i conclude that my WI-FI module is work and than i tried to scanned the AP and this is the result

> 
Cell 01 - Address: 00:0F:66:75:50:24
          ESSID:"Gandalf23"
          Protocol:IEEE 802.11bg
          Mode:Master
          Channel:9
          Encryption key:on
          Bit Rates:54 Mb/s
          Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
          Quality=66/100  Signal level=-48 dBm  Noise level=-67 dBm
          Extra: Last beacon: 1583ms ago


and i tried to connect to that AP using this command

> 
iwconfig eth1 ESSID Gandalf23 mode Ad-Hoc key restricted xxxxxxxxxx 


and then i tried to see the result and this the message

> 
eth1 unassociated ESSID:"Gandalf23"
Mode:Ad-Hoc Frequency=nan kHz Cell: Not-Associated
Bit Rate:0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thr:off Fragment thr:off
Encryption key:1234-5678-90 Security mode:restricted
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:1794 Missed beacon:0 


isn't it strange i'm able to connect with a correct wireless key but i got Link Quality zero for your information my laptop is close enough with the AP, can anybody help me solve this problem, thank b4

---

