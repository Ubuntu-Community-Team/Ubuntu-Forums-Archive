---
title: "Ubuntu 21.04, ROG Zephyrus G15 with extremly slow wireless speeds."
date: 2021-04-24
forum: Networking &amp; Wireless
---

### Post by smashace on 2021-04-24
Hi, I was wondering if anyone could help me out with my networking connection issues. my Intel AX200 wifi card is currently performing way below where it should be.

What I know:
 + network speeds are currently in the kilobytes for downloads, well below the limit for the 802.11 N router positioned 6ft away from me.
 + no one else in the household is currently trying to do any heavy downloads.

Install is relatively fresh, with only wine, lutris, steam, gnome tweaks, asusctl, and a handful of extensions to customize the UI.

info from wifi info script:
[ATTACH]288371[/ATTACH]

---

### Post by chili555 on 2021-04-24
```
wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'WesternDigital-11_5G' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"WesternDigital-11_5G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001eff5f685a7
                    Extra: Last beacon: 3984ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```Most Linux drivers hate hate hate TKIP. So do I. Hackers don't mind it as its relatively easy to crack.

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Is there any improvement?

---

### Post by smashace on 2021-04-26
already tested with REGDOMAIN, no change, will see if I can get router owner to fix that TKIP setting.

*EDIT*
got the encryption stuff fixed, and now I got around 11 - 12 megabytes download now. thanks!

---

