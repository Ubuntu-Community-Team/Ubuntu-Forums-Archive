---
title: "WLAN  TRENDnet TEW-421PC not working on Hardy"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by cirobr on 2008-05-10
Hello,

I have a notebook HP Pavillion ze4920 equipped with WLAN card TRENDnet TEW-421PC H/W:B1. It always worked smoothly under Ubuntu Gutsy (Windows XP driver from product CD and ndiswrapper).

After a clean installation of Hardy, WLAN card driver is reinstalled with ndiswrapper. Card is recognized by the system, which in turn detects all hot spots within range. When one is chosen, it keeps asking over and over the WPA password and login to network is not completed. Other Windows and Gutsy computers are able to login to all WLANs (none of them equipped with TRENDnet, however).

Updating to latest driver from TRENDnet home page and re installation resulted on same failure.

Any help to correct the problem is appreciated.

Regards,

Ciro.


Configuration info follows:

ciro@note1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





ciro@note1:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:4F:62:0D:E6:A3
                    ESSID:"vxcentro"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:08:A1:92:E7:7C
                    ESSID:"Wireless-G Router"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:15:E9:04:4C:A8
                    ESSID:"D-Link.CBR"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:13:46:C7:8C:D2
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by egstern on 2008-05-11
It seems something is not working possibly with ndiswrapper in hardy.  I upgraded a desktop system from gutsy 7.10 to hardy 8.04 over the network.  It uses a trendnet tew424ub usb wireless nic.  In gutsy, I was able use the nic with ndiswrapper to connect to my wpa encrypted network.  In hardy, when I try to connect the same way, the system has a hard lock-up at the time the connection applet shows about 26% completed.  This is consistently reproducible.  Since I upgraded, I still have my old kernel on the system.  If I boot the old kernel, I am able to fully connect.

The system in question is an AMD Athlon 2200 based system with a VIA chipset.  The old kernel that works with the nic is 2.6.22-14-generic.  The new kernel that doesn't work is 2.6.24-16-generic.  I have downloaded and built the most recent ndiswrapper from sourceforge, and also downloaded the most up-to-date windows driver.  Neither of those changed the lock-up behavior with the new kernel.

    egstern

---

