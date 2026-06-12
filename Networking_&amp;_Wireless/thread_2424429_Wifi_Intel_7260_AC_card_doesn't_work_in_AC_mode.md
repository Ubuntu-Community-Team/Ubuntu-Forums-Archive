---
title: "Wifi Intel 7260 AC card doesn't work in AC mode"
date: 2019-08-08
forum: Networking &amp; Wireless
---

### Post by coyote.us on 2019-08-08
Hi every one.

I have a laptop HP (envy 17-j150la), it have a Intel 7260BN wifi card and I changed it for a Intel 7260AC, it work fine but I can't do it work in AC mode.
Searching on google,  I found that, Intel give support until iwlwifi 17 version, and I have it....and it is working.

I have Ubuntu 18.04.3 LTS.

Thanks.....and.... Google helped me with the translation, my english is poor

---

### Post by praseodym on 2019-08-08
Please run the wireless script from the sticky thread and show the outputs

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by coyote.us on 2019-08-12
Hi....I didn't see the rules... sorry...

Here:

[http://paste.ubuntu.com/p/4Fd6fTJcvF/](http://paste.ubuntu.com/p/4Fd6fTJcvF/)

---

### Post by chili555 on 2019-08-12
> wlp7s0    Scan completed :
          Cell 01 - Address: <MAC 'VTR-9985602' [AC1]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"VTR-9985602"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003644654e57
                    Extra: Last beacon: 664ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

TKIP will not use very high throughput; i.e. 802.11ac.  Here is the confirmation from Intel themselves: [https://www.intel.com/content/www/us/en/support/articles/000006697/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000006697/network-and-i-o/wireless-networking.html)

As long as you are changing the settings in the router, check these additional settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

After making these changes, please tell us if there is any improvement.

---

### Post by coyote.us on 2019-08-12
Mmmm... but if run windows It's run on AC.

[IMG]https://photos.app.goo.gl/CnLgHpEH795qFiQHA[/IMG]

or......I'm wrong :confused:

---

### Post by coyote.us on 2019-08-12
[ATTACH=CONFIG]283787[/ATTACH]

I'm learning...how to.... insert images

---

### Post by chili555 on 2019-08-12
It's hard to tell. My 7260AC on Ubuntu says this:

```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:2B:B0:DC:45:xx
          Bit Rate=[COLOR="#FF0000"]866.7 Mb/s[/COLOR]   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:422   Missed beacon:0

```Perhaps the entirely different driver in Windows asks the router to auto-select CCMP, also known as AES instead of TKIP. Frankly, because TKIP is less secure than AES, I wouldn't recommend that anyone use it. I think router manufacturers are concerned about backwards compatibility, just in case Grandma shows up with her circa-2005 Gateway tower.

[https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)>  However, TKIP itself is no longer considered secure, and was deprecated in the 2012 revision of the 802.11 standard.

Have you tried to change the router? Is it better or worse?

A great many things work very well in Linux but not Windows and vice versa.

---

### Post by coyote.us on 2019-08-16
I can't use another one...it's from telecommunication company....and only have WPA-PSK and WPA-PSK/WPA2-PSK mode....is there another way to force the card to work in AC mode?

---

### Post by jeremy31 on 2019-08-16
Try ```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```
Reboot

---

### Post by coyote.us on 2019-08-17
Ok...
There is...

[http://paste.ubuntu.com/p/zKKKBHxrC7/](http://paste.ubuntu.com/p/zKKKBHxrC7/)

---

### Post by chili555 on 2019-08-17
Here is one reason that it isn't operating at AC speeds:> 
wlp7s0    IEEE 802.11  ESSID:"VTR-9985602"  
          Mode:Managed  [COLOR="#FF0000"]Frequency:2.437 GHz [/COLOR] Access Point: <MAC 'VTR-9985602' [AC1]>   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
[https://en.wikipedia.org/wiki/IEEE_802.11ac](https://en.wikipedia.org/wiki/IEEE_802.11ac)> IEEE 802.11ac is a wireless networking standard in the 802.11 set of protocols (which is part of the Wi-Fi networking family), providing high-throughput wireless local area networks (WLANs) ***on the 5 GHz band***. 

I notice that there is another node of the same router on 5 GHz:> 
SSID                   BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
VTR-9985602            <MAC 'VTR-9985602' [AC1]>  Infra  6     2437 MHz  130 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  yes     *      
WifiTelsur_XEBO_2      <MAC 'WifiTelsur_XEBO_2' [AC4]>  Infra  10    2457 MHz  130 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no             
WifiTelsur_XEBO        <MAC 'WifiTelsur_XEBO' [AC3]>  Infra  9     2452 MHz  130 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no             
--                     <MAC '--' [AN4]>  Infra  1     2412 MHz  405 Mbit/s  30      &#9602;___  WPA1 WPA2  no             
Aysen                  <MAC 'Aysen' [AC2]>  Infra  1     2412 MHz  405 Mbit/s  29      &#9602;___  WPA1 WPA2  no             
Wifi Cuellar Martinez  <MAC 'Wifi Cuellar Martinez' [AN6]>  Infra  11    2462 MHz  270 Mbit/s  19      &#9602;___  WPA1 WPA2  no             
WifiTelsur_5G_XEBO     <MAC 'WifiTelsur_5G_XEBO' [AC5]>  Infra  36    5180 MHz  270 Mbit/s  19      &#9602;___  WPA1 WPA2  no             
[COLOR="#FF0000"]VTR-9985602            <MAC 'VTR-9985602' [AC6]>  Infra  149   5745 MHz  405 Mbit/s  17      &#9602;___  WPA1 WPA2  no  [/COLOR]           
However, its signal strength is quite low. I doubt that you could connect to it in any event.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

I would ordinarily suggest that the 2.4 GHz and 5 GHz bands be renamed so as to prevent roaming from among them. I'd suggest something like VTR-9985602-2.4 and VTR-9985602-5. However, apparently the router is too far away to permit successful connection.

---

