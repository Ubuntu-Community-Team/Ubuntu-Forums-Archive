---
title: "Help with ndiswrapper"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by blah19 on 2007-01-06
Hello, 
I am tring to make my wireless card: WLI-CB-G54S by Buffalo Technology ([http://www.buffalotech.com/files/downloads/WLI-CB-G54S-Manual-v2.0-web.pdf](http://www.buffalotech.com/files/downloads/WLI-CB-G54S-Manual-v2.0-web.pdf)) work under ubuntu. I know it reconizeses the card because it says "No such device" under eth1 when I remove it. It does not, however, detect any network nor do any lights flash on the card. I was wondering if anyone knew the solution to this. I already installed ndiswrapper and tried to install the driver called "netcgb54.inf" there are, however, other inf files int the directory and I am not sure if it is the right one. (Although I belive it is because it forces some conditions when I  use that one.). It always shows disconnected when it is in. I double checked the ESSID and password. Could anyone help???

Edit: Also I ran "iwlist scan" and it yielded "eth1 No scan results" even though Im right next to it, and this other laptop is using it"

---

### Post by blah19 on 2007-01-06
anyone have any Idea??

---

### Post by zgornel on 2007-01-06
What are the results of:```
iwconfig && ifconfig
``` ```
ndiswrapper -l
```

---

### Post by blah19 on 2007-01-06
IW config:
[PHP]lo ...
eth...
eth1    IEEE 802.11b/g ESSID:off/any  Nickname:*Broadcom 4318*
          Mode:Managed Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0 Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx Invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0
sit0...
 [/PHP]

ifconfig
blank

ndiswrapper -l

[PHP]
Installed ndis drivers:
netcbg54        driver present
[/PHP]

---

### Post by zgornel on 2007-01-07
The driver seems to be installled ok... Try to associate manually to the access point ```
iwconfig eth1 ap xx:xx:xx:xx:xx:xx
``` or ```
iwconfig eth1 ap any
```
Also, check [this]("http://ubuntuforums.org/showthread.php?t=197102") HOWTO, it might help.

---

### Post by rbhigday on 2007-01-07
> **blah19 said:**
> IW config:
[PHP]lo ...
eth...
eth1    IEEE 802.11b/g ESSID:off/any  Nickname:*Broadcom 4318*
          Mode:Managed Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0 Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx Invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0
sit0...
 [/PHP]

ifconfig
blank

ndiswrapper -l

[PHP]
Installed ndis drivers:
netcbg54        driver present
[/PHP]

Unless I am missing something the wireless is connected to what appears to be a cable connection eth1 is a cable connection. You need wlan0 or "ap0?" (forgot the letters for the second one, but i am sure someone knows) for a wireless connection.  Do you have this under wireless in your network settings?

---

### Post by jglen490 on 2007-01-14
I just got through setting up one of those card.  They work well and will use either WEP security or WPA-PSK.  I originally had a reall problem with this card and with ndiswrapper - maybe a chicken or egg thing, I don't know ;) .

One thing that worked was going into the /etc/modprobe.d directory and adding an entry in the blacklist file to blacklist the bcm43xx driver loaded by the kernel.  The next thing was finding and loading Kwlan (I'm using Kubuntu, there is also a similar feature under Gnome) to configure the card and driver within my home network (using DHCP), and to setup wpa_supplicant.  Once I saved all my settings configured to wlan0 - and quit messing with it - it simply worked.

Now I really enjoy the freedom of my old IBM T20 laptop.  Hope this helps!!

---

