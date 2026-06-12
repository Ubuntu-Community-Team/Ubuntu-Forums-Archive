---
title: "intel centrino wireless-n 2200 drops connection, Ubuntu 16.04"
date: 2017-07-31
forum: Networking &amp; Wireless
---

### Post by dzanek on 2017-07-31
Hello!

My wifi gets disconnected quite often. To make it work again I have to turn it off and then on again. Also it works significantly slower than wifi on my smartphone ( 14 Mbps compared to 30 Mbps ). 
I did steps from [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) . 
My pastebin : [http://paste.ubuntu.com/25214644/](http://paste.ubuntu.com/25214644/)

What can be the cause?

---

### Post by chili555 on 2017-07-31
In your paste, we see:> Cell 01 - Address: <MAC 'FunBox-CDA9' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"FunBox-CDA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cd6e5dc3e
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKMany Linux divers, including iwlwifi and old Doc Chili hate TKIP.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and *certainly not* TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

