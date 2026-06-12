---
title: "Problems connecting to a specific Wi-Fi access point"
date: 2018-09-14
forum: Networking &amp; Wireless
---

### Post by eklypa on 2018-09-14
Hey. Recently, my laptop began to experience problems when connecting to a home Wi-Fi.
Sometimes it connects quickly, sometimes it takes about an hour. But when connected, the network works stably and without problems.
At the same time, the laptop connects to the access point of the mobile phone quickly and without problems. The mobile phone does not have problems connecting to the router
Here are the results of the script: [http://paste.ubuntu.com/p/N9McvwbNgy/](http://paste.ubuntu.com/p/N9McvwbNgy/) ("[COLOR=#000000]Kurpatov network" - my main Wi-Fi, "[/COLOR][COLOR=#000000]Kurpatov network Mini" - mobile access point[/COLOR])

[COLOR=#e6e6fa]PS: Sorry for Google Translate ^_^[/COLOR]

---

### Post by chili555 on 2018-09-14
> Cell 08 - Address: <MAC 'Kurpatov network' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Kurpatov network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000024d46d97
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKDid you pick channel 4 because you know it's an overlapped channel and you'd like to have as much interference and difficulty as possible? Or did you trust your router to auto select the channel? I suspect the latter. Here is everything wrong with that: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. You might also have better luck by renaming the network without a space in the name; I suggest Kurpatov_network or KurpatovNetwork or similar.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get

```
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda

```
Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Any improvement?

---

