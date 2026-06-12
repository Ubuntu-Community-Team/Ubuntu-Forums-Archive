---
title: "Ubuntu 19.04 on HP 8560p with Intel 6205 - intermittent connectivity - https://pasteb"
date: 2019-05-06
forum: Networking &amp; Wireless
---

### Post by fox-q on 2019-05-06
Hi guys,

Wifi connectivity on a relatively fresh install (~one week old) has suddenly become intermittent or non-functional. 
Connection continually drops and reconnects, or fails entirely. *[edit]* Connectivity in Live-session is flawless.
I would be grateful if someone could point me in the right direction.

Best wishes and thanks!



[LIST]
[*]**System:** HP 8560p 
[*]**OS:** KUbuntu 19.04 
[*]**wireless-info:** [https://pastebin.com/axxiKTCK](https://pastebin.com/axxiKTCK) 
[/LIST]

---

### Post by chili555 on 2019-05-06
We notice this:

> Cell 01 - Address: <MAC '53y9j7a5' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"53y9j7a5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fb8976800
                    Extra: Last beacon: 136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
 Your driver and old Chili hate hate hate TKIP. We also hate any auto select between WPA and WPA2. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Reboot and let us hear the result.

---

### Post by fox-q on 2019-05-06
[FONT=Univers LT Std 55]Hi Chilli, thanks for the speedy reply![/FONT]
  
 
  [FONT=Univers LT Std 55]After following your recommendations _and_ downgrading netplan.io from v4.1 > 4.0, connectivity works, well... slightly better, but is still slow and erratic. With v4.1 it doesn&#8217;t work at all.[/FONT]
  
 
  [FONT=Univers LT Std 55]However, transfer rates are about 0-100kb/s (down from 1.5-3mb/s) and the connection drops frequently and often stays down.[/FONT]

  
 
  [FONT=Univers LT Std 55]Coming from Manjaro my first instinct was to downgrade netplan.io, but that by itself is clearly insufficient. My sense is that it ought to be a package based issue because connectivity in the live-usb session is flawless, as was the system prior to yesterday (Sunday).[/FONT]

---

### Post by chili555 on 2019-05-07
>  my first instinct was to downgrade netplan.ioWhy?? Are you even using netplan? Typically, in a desktop installation, netplan turns everything over to Network Manager.

May we see an updated wireless info paste? Also:```
cat /etc/netplan/*.yaml
```

---

### Post by fox-q on 2019-05-08
I was able to make it work by installing Ubuntu 18.04 LTS with KDE Neon, figuring this would be quicker than troubleshooting.  
 
 
 I&#8217;d like something that just works so I can avoid unexpected downtime, which was my reason for  moving away from a rolling release.
 
 
 Happily it seems ok now, with the caveat that after each login it does this little dance where it&#8217;ll activate-deactivate-activate wifi in a quick 1-2-3 succession, but then it remains stable. Haven&#8217;t experienced any drops.

 
 
 Thanks for your time Chili, I am grateful!

---

