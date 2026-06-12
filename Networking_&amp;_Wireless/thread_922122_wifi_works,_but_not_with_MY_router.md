---
title: "wifi works, but not with MY router"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by peas on my plate on 2008-09-17
My wireless card works, but I cannot get it to connect to my netgear WPN824 router.  I am running Hardy on a Dell Vostro 1400.  My wife is running Hardy on her Latitude and can connect to the wireless network without a problem.  When booted in XP, my laptop connects to my wireless network as well.  I can connect to other unsecured networks nearby in Hardy on my machine.  

Here is my network info as listed by iwlist scan:
eth1      Scan completed :
          Cell 01 - Address: 00:1E:C7:92:DB:F9
                    ESSID:"2WIRE847"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

And this is what I get from iwconfig:
richard@ortsy:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"bolweevil"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=-40 dBm  Noise level=-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:63  Rx invalid frag:0
          Tx excessive retries:31  Invalid misc:0   Missed beacon:0

Should I try turning encryption off, or should this not make a difference?

---

### Post by peas on my plate on 2008-09-17
bump.

---

