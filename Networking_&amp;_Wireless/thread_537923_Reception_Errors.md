---
title: "Reception Errors"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by keylime on 2007-08-29
I have a HP NC4200 coupled with an Intel 2200 wireless chipset.

I have been able to install firmware and driver for this device, and I am able to set a static IP and have it talk to our router. However it is unable to get to the Internet.

Here's what my system tells me:

[   22.320000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   22.320000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   22.320000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   24.568000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

eth1      Scan completed :
          Cell 01 - Address: 00:16:47:75:17:40
                    ESSID:"sectbstcur"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 13324ms ago
          Cell 02 - Address: 00:16:47:75:17:41
                    ESSID:"tbstcur"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    Extra: Last beacon: 13284ms ago
          Cell 03 - Address: 02:18:DE:00:00:7B
                    ESSID:"Wayport_Access"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    Extra: Last beacon: 44ms ago
          Cell 04 - Address: E6:66:0F:07:C4:FF
                    ESSID:"Free Public WiFi"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    Extra: Last beacon: 52ms ago
          Cell 05 - Address: 00:13:C4:CE:80:60
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 52ms ago
          Cell 06 - Address: 00:16:47:75:25:41
                    ESSID:"tbstcur"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    Extra: Last beacon: 84ms ago
          Cell 07 - Address: 02:12:F0:44:10:6E
                    ESSID:"Free Public WiFi"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:10
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    Extra: Last beacon: 2540ms ago
          Cell 08 - Address: 00:16:47:75:25:40
                    ESSID:"sectbstcur"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 136ms ago

eth1      IEEE 802.11g  ESSID:"tbstcur"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:47:75:25:41   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=-64 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:184  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When checking in Network Tools I learned that there are a lot of reception errors. It's nearly dropping each packet.

Any ideas?

---

