---
title: "Vaio VGN AW31M droping wifi after upgrade to 16.04LTS"
date: 2017-05-25
forum: Networking &amp; Wireless
---

### Post by damo-c on 2017-05-25
My wifi was fine until I upgraded to 16.04LTS but now I have to occasionally reset it after it stalls.
I am a newbie and can follow instructions but my knowledge is limited.
This is the result of the wireless-info script.

[http://paste.ubuntu.com/24654754/](http://paste.ubuntu.com/24654754/)

TIA

---

### Post by wildmanne39 on 2017-05-25
I have that issue sometimes with 5ghz also, I recommend setting your channel to 40 in the router and if you can rename one of your connections so your wifi is less likely to roam between the two.

Also your 2.4 ghz network has a lot stronger signal, the 5ghz barely has enough to connect.

---

### Post by damo-c on 2017-05-28
Thanks for responding...
All was ok until I upgraded to 16.04 so I as assuming that therein lies he problem.
I am considering re-installing my previous version because this does not seem fixable for me.

---

### Post by wildmanne39 on 2017-05-29
Did you do what I recommended? if so what is the outcome? still having issues run the wireless script again so we can see what else we can do, not sure going backwards will help.

---

### Post by chili555 on 2017-05-29
> wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Artemis' [AC1]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Artemis"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2d8f011fa
                    Extra: Last beacon: 180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKThe Wild Man also hopes you will set your router to WPA2-AES and not any mixed mode and certainly not TKIP. Wild Man, Doc Chili and your driver iwlwifi hate hate hate TKIP.

I'd rename the channels to Artemis2.4 and Artemis5 or some such. The Wild Man is quite correct about roaming and dropping between the SSIDs.

---

