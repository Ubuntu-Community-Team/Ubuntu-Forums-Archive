---
title: "Wireless ipw2200 ubuntu 6.06 dapper WPA !!"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by argon_001 on 2006-08-27
Hi Guys,

Can any one help me to sort out what is wrong with my wireless ipw2200 settings. I have installed the latest Ubuntu 6.06 dapper on my laptop. I can connect to wireless netwrok when I disable the WPA security on my router from my laptop but when I enable the WPA I no longer can connect to my router or even AP. 

I get the following messages when I send the the commands:
 iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:E7:2C:FB
                    ESSID:"MyHomeD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=93/100  Signal level=-34 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 364ms ago
          Cell 02 - Address: 00:0D:0B:14:F2:0B
                    ESSID:"49A37729454111846B83E21F2F508C81"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=70/100  Signal level=-58 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 296ms ago
          Cell 03 - Address: 00:12:17:74:E1:94
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=35/100  Signal level=-79 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 460ms ago
          Cell 04 - Address: 00:13:46:5A:60:95
                    ESSID:"D-link"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=23/100  Signal level=-85 dBm
                    Extra: Last beacon: 2600ms ago

------------------------- iwconfig eth1
eth1      unassociated  ESSID:"MyHomeD"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:476   Missed beacon:0
---------------------------------
sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:12:f0:2a:7a:59
Sending on   LPF/eth1/00:12:f0:2a:7a:59
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.11.13
PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.

--- 192.168.11.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

---------------
Please let me if you have already solved this problem. 
Thanks in advance

argon

---

### Post by XioNoX on 2006-08-27
install just network-manager-gnome and restart

---

### Post by argon_001 on 2006-08-29
Hi,

I have installed network-manager-gnome and restarted my laptop but and tried to connect my WPA enabled wireless network but couldn't do it sucessfully. 

Any suggestions??](*,) 

Argon

---

