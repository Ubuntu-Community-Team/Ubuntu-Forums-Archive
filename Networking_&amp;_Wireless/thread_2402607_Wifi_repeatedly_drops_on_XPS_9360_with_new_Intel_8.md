---
title: "Wifi repeatedly drops on XPS 9360 with new Intel 8265 wifi card"
date: 2018-10-02
forum: Networking &amp; Wireless
---

### Post by chessguy on 2018-10-02
Hi, 

I've had frequent problems with my wifi on a dual boot Ubuntu-Windows XPS 13 9360.

After many other attempts, I replaced the wifi card to an Intel 8265 (as recommened just about anywhere). But my wifi is still dropping all the time. (It doesn't say disconnected but just won't download)

Here is the wireless info from the script on this site: [https://pastebin.com/1GpAx8J4](https://pastebin.com/1GpAx8J4)

Thanks so so much!

---

### Post by praseodym on 2018-10-03
Obviously, you installed the proprietary Broadcom STA driver:
```

sudo apt-get remove --purge bcmwl-kernel-source
```
Reboot

---

### Post by chessguy on 2018-10-12
Thanks @praseodym for the help. It's definitely helped but my wifi is definitely still dropping. Any ideas? (Also all v non obvious to me :) )

---

### Post by chili555 on 2018-10-12
>  Cell 01 - Address: <MAC '[COLOR="#FF0000"]BTHub6-RF23[/COLOR]' [AC1]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"BTHub6-RF23"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cb59b33de
                    Extra: Last beacon: 312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '[COLOR="#FF0000"]BTHub6-RF23[/COLOR]' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"BTHub6-RF23"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cb3a4b677
                    Extra: Last beacon: 972ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKIs it dropping because it is roaming from among the two SSIDs with the same name? Are you able to rename one of them; perhaps the 5 GHz segment to BTHub6-RF23-5?

I also notice that there are three SSIDs on channel 44. If you are able, I suggest that you change to channel 48.

If not, I suggest that you ask Network Manager to prefer the 5 GHz segment by referring to its MAC address like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

