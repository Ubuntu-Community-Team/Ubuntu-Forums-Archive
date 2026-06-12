---
title: "wireless does not work with Hardy heron 8.04 TLS"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Vinux75 on 2008-05-12
Dear Forum,

I had recently upgraded to Hardy Heron 8.04 from Gusty 7.10. The wirless LAN was working fine with the Gusty 7.10. But after upgrading to Hardy I have not been able to connect to wireless network. I am able to see the wireless network but the connection attempt fails, no IP address is obtained. I am using the WLAN card wl 138 from Asus.

Any help will be greatly appreciated.


Please find given below some information extracted from the system
---------------------------------------------------------------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"WLAN-14092202"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:12:BF:92:0A:91   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
---------------------------------------------------------------------
iwlist eth1 scan

eth1      Scan completed :
          Cell 01 - Address: 00:19:CB:59:B7:74
                    ESSID:"o2DSL"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/100  Signal level=-43 dBm  Noise level=-47 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000069913201b9
          Cell 02 - Address: 00:12:BF:92:0A:91
                    ESSID:"WLAN-14092202"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/100  Signal level=-43 dBm  Noise level=-47 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000002634aa181
 -------------------------------------------------------------------------
eth1      Scan completed :
          Cell 01 - Address: 00:19:CB:59:B7:74
                    ESSID:"o2DSL"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/100  Signal level=-43 dBm  Noise level=-47 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000069913201b9
          Cell 02 - Address: 00:12:BF:92:0A:91
                    ESSID:"WLAN-14092202"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/100  Signal level=-43 dBm  Noise level=-47 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000002634aa181
          Cell 03 - Address: 00:1D:19:39:70:75
                    ESSID:"WLAN-397040"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=65/100  Signal level=-48 dBm  Noise level=-47 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000747e0d5182
----------------------------------------------------------------------
dmesg

[ 3764.708589] eth1: Initial auth_alg=0
[ 3764.708591] eth1: authenticate with AP 00:12:bf:92:0a:91
[ 3764.907144] eth1: authenticate with AP 00:12:bf:92:0a:91
[ 3765.107114] eth1: authenticate with AP 00:12:bf:92:0a:91
[ 3765.308057] eth1: authentication with AP 00:12:bf:92:0a:91 timed out

---

### Post by Ayuthia on 2008-05-12
Can you post your lspci -nn info?  That will provide us more detail about your wireless card.

---

### Post by Vinux75 on 2008-05-12
Hi,

The post under the title 
"Reload this Page  [ubuntu] Broadcom Wireless Setup for Hardy (Step by step)" by alex_kent_18 helped me to connect to the wirless network in Hardy.
Thanks to alex. 

Thankyou Ayuthia, my wirless network is working now :)

---

