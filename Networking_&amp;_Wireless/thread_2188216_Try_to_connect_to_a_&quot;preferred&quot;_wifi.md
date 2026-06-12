---
title: "Try to connect to a &quot;preferred&quot; wifi"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by ^_Pepe_^ on 2013-11-16
Hi all,

I have 3 different SSID's at home (several Access Points), and when I open my Thinkpad it tries to connect to one of them...

But...it's usually the one which has less dB's :(. I couldn't find a pattern here. Not the last, nor the stronger.

Question. Is there any clue to "force" Network Manager to try first one network???

Thanks
^_Pepe_^

---

### Post by chili555 on 2013-11-16
I suggest you try setting the MAC address of the access point you wish to connect to in Network Manager under BSSID. Check off 'Connect Automatically.' Please see: [http://img.xrmb2.net/images/647404.png](http://img.xrmb2.net/images/647404.png)

You can find the MAC address here:```
iwconfig
```> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: [COLOR="#FF0000"]88:D7:99:41:54:EE[/COLOR]   
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0


---

### Post by ^_Pepe_^ on 2013-11-18
Thanks for the information! 

It seems to work!

^_Pepe_^

---

