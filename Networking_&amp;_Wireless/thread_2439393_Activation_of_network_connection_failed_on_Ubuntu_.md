---
title: "Activation of network connection failed on Ubuntu 18.04 LTS"
date: 2020-03-27
forum: Networking &amp; Wireless
---

### Post by antikas1989 on 2020-03-27
I've been happily using wifi for years on my ubuntu machine but last night it apparently stopped working.
I've rebooted several times, ensured everything is updated and the problem persists.  I can still connect to my phone to use the hotspot feature (which is what I'm using to post this) but I cannot connect to the wifi.  My phone, tablet and partner's macbook can all still connect to the wifi which seems to be working fine.

When I try to connect after a while I see a notification that reads Activation of network connection failed.  

I've run the wireless-info script and the results are on pastebin here [https://pastebin.com/aXZT1EEN](https://pastebin.com/aXZT1EEN)

I am using an ASUS UX303UA Notebook and 18.04 LTS

The closest other post I've found on this forum (RE wifi working and then suddenly stopping with this error message) is [https://ubuntuforums.org/showthread.php?t=2421381](https://ubuntuforums.org/showthread.php?t=2421381)
I don't know how relevant that is, my syslog doesn't look similar to what is there but I don't know much about how to read the syslog.  I don't understand the solution so I haven't attempted it.

Not sure if this is relevant:  I was connected to my university VPN through openconnect at the time of disconnect.  Initially I could reconnect to my wifi by turning wifi off then on again, but after a minute or two the internet would stop working.  I did that 2 or 3 times before I started getting the current error message and haven't been able to connect to the wifi since.  As I said that's after multiple reboots, updating packages on my machine etc.  I also tried forgetting the network and reconnecting.

---

### Post by chili555 on 2020-03-27
Here is a serious problem:

> VM9166893           <MAC 'VM9166893' [AC3]>  Infra  11    2462 MHz  130 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2    no          
VM9166893           <MAC 'VM9166893' [AC6]>  Infra  44    5220 MHz  405 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no  

There are two access points with the same name.One is the 2.4 gHz segment and the other is the 5 gHz segment of, I assume, the same router. I am quite confident that your wireless device is roaming among the two looking for a better connection, much like my ex-girlfriend.

I suggest that you rename one or both. May I suggest VM9166893-2.4 and VM9166893-5?

Next, I see this:

> Cell 06 - Address: <MAC 'VM9166893' [AC6]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"VM9166893"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003066765cde
                    Extra: Last beacon: 232ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Any improvement?

---

