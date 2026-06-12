---
title: "wireless failure after upgrade to 14.04 LTS"
date: 2014-09-03
forum: Networking &amp; Wireless
---

### Post by ac7nj on 2014-09-03
here is some information from terminal 
randy@AC7NJ:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: B8:9B:C9:21:B7:F8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"HOME-B7F8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 0009484F4D452D42374638
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880B89BC921B7F8103C0001011049000600372A000120
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1AEE1117FFFFFF00010000000000000000000000000F0000000000
                    IE: Unknown: 3D160B070500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030020127A
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 3E0100
                    IE: Unknown: 0B05020020127A
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD....

randy@AC7NJ:~$ sudo iwconfig wlan0 essid Home-B7F8 key s:22097842
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

what am I doing wrong? manager keeps asking for key over and over so I tried to connect manualy in bash as you can see that failed also

Randy

---

### Post by varunendra on 2014-09-04
Please change the encryption in your router/Access-Point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP which should be avoided due to being inferior, inefficient and added complexity. Reboot the router after saving the change.

If the above change alone doesn't fix the issue, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

