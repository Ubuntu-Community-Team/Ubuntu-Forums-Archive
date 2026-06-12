---
title: "Old Trendnet wireless card vs new routers"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by SirChuck on 2008-10-01
This sounds crazy, so I am sure I forgot to do something stupid. However, I am using a Trendnet TEW-226PC wireless adapter on my Toshiba notebook and I can't get it to see 6 out of the 7 available networks. 

Wierd right? The only one I have been able to connect to through Ubuntu 8.04 Hardy Heron, was a the "linksys" router with no security.Here are three from a (iwlist scan) I can connect to the first one, but none of the others. The last one with no essid is mine but my router is set not to report the essid. The Xiocom-Gptow1.1b is essentially the same as the linksys and yet I cant connect to it. 

          Cell 01 - Address: 00:16:B6:3C:8A:A4
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:15:6D:63:D2:76
                    ESSID:"Xiocom-Gptow1.1b"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:1E:52:7B:71:79
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-104
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : WEP-104
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

So, any ideas? The only thing I can think at this point is my card running the ndiswrapper drivers cant work with the newer routers, The card can connect without a problem on my windows partition. I am using an Air Port Extreme Base Station.

Also wierd, the command "sudo iwconfig wlan0 essid homeNTW" which is my essid, will not give any errors but when you do iwconfig it remains at essid: off/any. 

Well any suggestions would be great, its nice that the linksys guy is sharing his network with me so I can wright this but i'd prefer my own cable connection. :)

---

### Post by SirChuck on 2008-10-01
This isn't the solution I was looking for but it works, so maybe it will help you too.

I installed WICD [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/").

In hopes it was something network manager was doing wrong, but still I could only connect to the one network.

So I switched my router to broadcast its essid again and still no luck.

The fix, I changed my routers essid name to "linksnot" and it worked!!!!! 

I have had difficulty in the past with ubuntu's network manager seeing a network with a funny name like mine "homeNTW". I used a trick to have it see the name by typeing "homeNTW     /" which allowed it to get the essid right.

But wow, could this really have been the stumbling block? the name of the essid on the router? I didn't think it had to be case sensitive or a certain amount of letters. 

Anyway router with "linksnot" works.

I'd love to hear your comments on why this fixed my problem lol.

---

