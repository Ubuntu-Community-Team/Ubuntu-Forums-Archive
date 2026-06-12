---
title: "Ubuntu 17.10 - Centrino Wireless-N 1000 - Thinkpad E-520"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by malcolmjs on 2017-12-11
Hi all,

I'm very new to Ubuntu, having just migrated from windows 7, and have tested 16.04 and 17.10 and even Linux Mint but have settled with 17.10 as my preference (for the programming tasks I will need to do, everything runs much more quickly).

With all of the Linux environments I have tested, I have experienced the same problem. Accessing the internet via my wireless adapter is either very slow or complete stop. I'm getting ~75Mbps with the wired connection. Maximum of 1 Mbps with wireless (sometimes nothing).

[http://paste.ubuntu.com/26163189/](http://paste.ubuntu.com/26163189/)

I hope the I have used this pastebin correctly! I have followed the advice on a number of fora from others who have posted similar questions but nothing helped. If anybody has any advice I'd be most happy to hear.

Many thanks,

Malcolm

---

### Post by chili555 on 2017-12-11
> Cell 01 - Address: <MAC 'UPC2649621' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"UPC2649621"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b8d8efb3
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK"Good morning! I speak four different languages, WPA and WPA2 and TKIP and CCMP. Sometimes, I speak all of them at the same time. Can you understand me clearly now??"

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Did I say that I hate TKIP?

Here is my wireless speed test using an Intel card: [http://beta.speedtest.net/result/6869486955](http://beta.speedtest.net/result/6869486955)

---

### Post by malcolmjs on 2017-12-11
Hi chilli555,

Your suggestions have really helped me get up to speed... I'm now at 30Mbps on wifi which is sufficient for everything I would want to do.

Thanks,

Malcolm

---

