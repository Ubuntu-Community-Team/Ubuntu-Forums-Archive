---
title: "Wi-fi bridging"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by bdoe on 2007-08-25
I've got a Belkin F5D7230-4 v.2000 wireless router, and I'm using a Belkin F5D7130 v.1121 AP as a bridge.  Everything was working properly when I was using WEP, but following the advice of someone here who pointed out that WEP was insecure, I converted to WPA.  I set both the router and the bridge for WPA, using the same keycode on both, set up my wireless card, and - I could talk to the bridge, but the bridge was no longer talking to the router.  I turned off the bridge, and I could connect to the router and access the internet again.  For some reason, the bridge and router are no longer talking to each other.  The only things I had changed in both were changing from WEP to WPA-PSK, entered the same keycode in both, and this is what happened.  Does anyone know how to get these two talking again?  Or am I going to have to go back to WEP?

Here's my iwlist scan output:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:33:B0:AB
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-28 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 108ms ago
          Cell 02 - Address: 00:11:50:3B:9E:33
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-50 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 68ms ago
          Cell 03 - Address: 00:11:50:33:B0:AB
                    ESSID:"WDNT"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-29 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 5800ms ago
          Cell 04 - Address: 00:11:50:3B:9E:33
                    ESSID:"WDNT"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-50 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 5792ms ago
```If this helps, for some reason it's listing four cells (I only have two), and cells 3 and 4 are reporting my SSID, even though it's not broadcasting.  Cells 1 and 3 are my bridge, cells 2 and 4 are my router.

Any ideas?

Edit:  I ran iwlist again, and the last two cells dropped off.

---

