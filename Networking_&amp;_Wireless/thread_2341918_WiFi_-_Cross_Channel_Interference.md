---
title: "WiFi - Cross Channel Interference?"
date: 2016-11-02
forum: Networking &amp; Wireless
---

### Post by Mel_Blakey on 2016-11-02
A few months ago I bought a new Lenovo ideapad 100. After a short trial of dual booting I wiped Win10 off and installed Ubuntu 16.06.
It's been fantastic. Everything working fine, even the WiFi has been flying along. That is until I recommended my set-up [Huawei MiFi unit on UK 3 Mobile Network] to my neighbour.

Since he got his on Saturday, my WiFi signal strength / speed has deteriorated.

I had my unit fixed on channel 11 and when I checked with 'Wifi Radar' I found that my neighbour is on channel 9. I have tried channels 1,3,5,6,7,13 and none offered any improvement, so I'm back on 11. 
It shows a vast improvement when his Mifi is turned off. So, it is not a coincidence.

Anyone got any suggestions???

Attached is a Screenshot from Wifi Radar with my neighbours MiFi turned off (mine is highlighted) and wireless-infor.tar.gz

Thanks!

[ATTACH=CONFIG]271918[/ATTACH]

[ATTACH]271919[/ATTACH]

---

### Post by chili555 on 2016-11-02
> wlp4s0    Scan completed :
          Cell 01 - Address: <MAC '3MobileWiFi-b1e1' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"3MobileWiFi-b1e1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002faf1987b
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKMost Linux drivers, and everyone at Chili's house, hate TKIP!!! At the very least, it is not as secure as AES, also known as CCMP.

WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. In my own case, N speeds are actually *better* set to 20 MHz, although that may be specific to my router.

Reboot the router and let us know if connectivity is improved.

---

### Post by mörgæs on 2016-11-02
Would it be worth a try to disable 2,4 GHz in the router, using only 5 GHz?

---

### Post by chili555 on 2016-11-03
> **mörgæs said:**
> Would it be worth a try to disable 2,4 GHz in the router, using only 5 GHz?His wireless-info says that his available channels are 1 through 13 only. In contrast, N-capable machines report:```
wlp3s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz

```

---

### Post by Mel_Blakey on 2016-11-06
> **chili555 said:**
> Most Linux drivers, and everyone at Chili's house, hate TKIP!!! At the very least, it is not as secure as AES, also known as CCMP.

I forgot about your hatred of TKIP.

The settings available to me are:
[U][B]
802.11 authentication[/B][/U]
Auto
Open
Share
WPA-PSk
WPA2-PSK
WPA/WPA2-PSK

_**Encryption mode**_
AES
TKIP
AES+TKIP


I have settled for WPA2-PSK & AES and it's pretty good now!

Changing from 802.11b/g/n to 802.11b/g seems to have no effect.


Thanks for both replies and big apologies for not responding sooner.

---

### Post by chili555 on 2016-11-06
> I have settled for WPA2-PSK & AES and it's pretty good now!Awesome! Glad it's working. Post back if we can help further.

---

