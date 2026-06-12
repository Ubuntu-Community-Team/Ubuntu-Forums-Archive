---
title: "LinkSYS WMP54G config problems"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by Embalmedlenin on 2005-08-10
Ok i just installed wmp54g v4 on my computer installed ndiswrapper configured it and installed drivers for the card. Anyway its not allowing me to connect to the connect even though it reconised the wireless network since i scaned for them heres what i get when i type ifconfig
I didnt paste my other interface because it activated so i could write this post.
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:302322 (295.2 KiB)  TX bytes:302322 (295.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:8B:7D:B7
          inet6 addr: fe80::212:17ff:fe8b:7db7/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:d4000000-d4001fff


heres the output of iwconfig wlan0

wlan0     IEEE 802.11g  ESSID:"Wireless for $5/m Billy 818-xxxx"
          Mode:Auto  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-120 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:ABCD-EABC-DE   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-42 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:205   Missed beacon:0
any other information just ask and ill post it.
I don't know what else to try
any help appreciated

David

---

