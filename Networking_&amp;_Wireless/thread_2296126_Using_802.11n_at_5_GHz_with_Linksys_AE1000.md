---
title: "Using 802.11n at 5 GHz with Linksys AE1000"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by patrice3 on 2015-09-23
[FONT=arial][SIZE=1]Hi all,
I'm trying to use a Linksys AE1000 802.11 abgn WiFi adapter on the 5 GHz band but it does not detect the SSID on the band. The embedded chipset is the:
lsusb
Bus 002 Device 005: ID 13b1:002f Linksys AE1000 v1 802.11n [[COLOR=#FF0000]Ralink RT3572[/COLOR]].[/SIZE][/FONT]
[FONT=arial][SIZE=1]The result of the iwlist scanning command is the following:
patrice@patrice-Inspiron-620:~$ iwlist scanning
wlan1     Scan completed :
          Cell 01 - Address: 6C:2E:85:B6:2C:A8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Livebox-2CA8_24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000150f5b42e9
                    Extra: Last beacon: 55592ms ago
                    IE: Unknown: 000F4C697665626F782D324341385F3234
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 341606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8F0050F204104A0001101044000102103B000103104700103D4A394C3F3CF93DF94A483F074A394C10210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E31104200094C4B313330353046461054000800060050F204000110110000100800020006103C0001011049000600372A000120

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

patrice@patrice-Inspiron-620:~$ 


Do you have any idea why the 5GHz is not detected.
Of course, if it not detected, I cannot use it :(, and I really need it !
Thank you very much in advance.
Patrice[/SIZE][/FONT]

---

### Post by patrice3 on 2015-09-23
Ok, after waiting a while I can see the 5 GHz SSID. I think I have not waited enough to get it, but when I tried to connect to the wl network it did not work. It is apparently due to the fact that the box was configured on the DFS band (channel 112). As soon as I have modified the channel to the non dfs, lower 5 GHz band on channel 36 I was able to connect.
Do you know if the driver rt2800usb has some restriction about the selected band ?

Thank you very much.
Patrice

---

