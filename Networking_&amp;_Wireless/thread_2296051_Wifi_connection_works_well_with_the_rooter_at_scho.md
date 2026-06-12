---
title: "Wifi connection works well with the rooter at school but it is uneven at home"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by Calin_Goina on 2015-09-23
I have Ubuntu 14.04 clean install on a laptop Dell Inspiron N5030 (in parallel with Win 7).

My wireless connection works seamlessly at the university where I work, but when I want
to use Ubuntu at home, the connection is established but the data 'goes through' only from
time to time. I see that a couple of minutes there is no traffic, the browser is unable to open
any site, then the site I am browsing does load up, only to be followed by another full minutes 
with zero transfer, so I am staring at the browser, waiting..

What is weird is that, with the same router, under Win 7, I have a very good internet 
experience, flawless traffic.

I have a wifi router D-Link GO-RT-N150

My internet provider requires an PPPoE connection.

It can't be a hardware problem, since the same laptop, running Ubuntu, does not
have any problems with the wifi connection at work - there internet works great.

Please, if you have any suggestions...

---

### Post by chili555 on 2015-09-24
Let's see how the router at home is set up:```
sudo iwlist wlan0 scan
```Please omit all the other networks except yours.

Thanks.

---

### Post by Calin_Goina on 2015-09-28
I must be doing something wrong, for when I paste in Terminal your line
I get a lot of data on the wifi connections of my building, but it stats from cell nr 7 (through 20)
 BUT and there is no data on my own connection.. which I guess must be among the first?

for example that's what I get
Quality=22/70  Signal level=-88 dBm 
                    Encryption key:on
                    ESSID:"HUAWEI-ws9m"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008777ba8b99d
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000B4855415745492D7773396D
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706414C20010E1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AF0181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 90:17:AC:72:20:58
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-96 dBm 
                    Encryption key:on
                    ESSID:"HUAWEI-KPeu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006ae77d3b196
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 000B4855415745492D4B506575
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706414C20010E1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AF0181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: C8:3A:35:07:69:D0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm 
                    Encryption key:on
                    ESSID:"apja"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
...and so on, and so on...




> **chili555 said:**
> Let's see how the router at home is set up:```
sudo iwlist wlan0 scan
```Please omit all the other networks except yours.

Thanks.

---

