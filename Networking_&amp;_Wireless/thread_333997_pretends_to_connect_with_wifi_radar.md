---
title: "pretends to connect with wifi radar"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by la-sorga on 2007-01-08
I have installed my drivers for my intel pro wireless 2200bg, When I use wifi rader I am able to see the local wifi connections I try to connect it says its retrievein the ip but doesnt do anythin!!! Any ideas?
I have an acer aspire 1650, I have also installed acerhk so the buttons on the front of my laptop work to turn the wifi card on and off (thouh the led doesnt work!) I dont know what to do!?!? Can some one help me, please
La Sorg](*,) a
ps. my wifi comes up as eth1, instaed of wlan0 does this make any difference?

---

### Post by la-sorga on 2007-01-08
when I type iwconfig I get:
lo        no wireless extensions.

eth1      unassociated  ESSID:"WiFi"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
 and when I type iwlist eth1 scanning I get:
eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:97:2E:82
                    ESSID:"BTHomeHub-C207"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=64/100  Signal level=-62 dBm
                    Extra: Last beacon: 320ms ago
          Cell 02 - Address: 00:0F:B5:C6:49:9A
                    ESSID:"WiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=94/100  Signal level=-33 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 112ms ago

but can not connect to either of them

---

### Post by la-sorga on 2007-01-08
one other thing in my connection properties when I go to support for the wifi eth1 it says that its an ethernet device!!!!!!! does that matter or not?

---

### Post by rbhigday on 2007-01-08
your wireless should be under wlan0 or ath0(?) I can never remember the letters for the other one, mostly because I have a wlan0.

You may want to check to see if you got set up under wired instead of wireless.

---

### Post by rbhigday on 2007-01-08
> **la-sorga said:**
> when I type iwconfig I get:
lo        no wireless extensions.

eth1      unassociated  ESSID:"WiFi"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
 and when I type iwlist eth1 scanning I get:
eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:97:2E:82
                    ESSID:"BTHomeHub-C207"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=64/100  Signal level=-62 dBm
                    Extra: Last beacon: 320ms ago
          Cell 02 - Address: 00:0F:B5:C6:49:9A
                    ESSID:"WiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=94/100  Signal level=-33 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 112ms ago

but can not connect to either of them

A suggestion next time you may want to put this in a code box you can do the by clicking the # symbol on the message box, that way smiley faces do not end up in your code. :)

---

### Post by la-sorga on 2007-01-08
how would I go about seein if I have set up under wired instead of wireless?
thanx a million

---

### Post by la-sorga on 2007-01-09
how would i see if it set as wired or wirless? and how would i change fron eth1 to wlan0 and is it realy necessary? my friend who has experience in linux says its not exactly
thanx a million

---

