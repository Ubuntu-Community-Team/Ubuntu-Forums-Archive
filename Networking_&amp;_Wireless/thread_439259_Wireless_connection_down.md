---
title: "Wireless connection down"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by Loki-59 on 2007-05-10
hi !

i'm using feisty with a pci wireless card: WMP54 (RT2500)
I use WEP security since six month. all is ok.
Yesterday, i have modified my /etc/network/interfaces files for use WPA with this parameters:
```
post-up iwconfig ra0 essid "essid"
post-up iwconfig ra0 mode managed
post-up iwpriv ra0 set Channel=13 # channel
post-up iwpriv ra0 set AuthMode=WPAPSK
post-up iwpriv ra0 set EncrypType=TKIP
post-up iwpriv ra0 set WPAPSK="WPA-Key"
```
My connexion it was ok with these parameters  but today my connexion is down.
I tray to reconnect with a WEP key but it don't work too !
more info:
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
ra0       Scan completed :
          Cell 01 - Address: 1E:08:BC:8E:F4:5C
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-50 dBm  Noise level:-192 dBm
          Cell 02 - Address: 1E:08:BC:8E:F4:5D
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-49 dBm  Noise level:-192 dBm
          Cell 03 - Address: 1E:08:BC:8E:F4:5E
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-49 dBm  Noise level:-192 dBm
          Cell 04 - Address: 1E:08:BC:8E:F4:5F
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-50 dBm  Noise level:-192 dBm
```

Mac address are strange, it's not the mac address of my wireless device !

ps: excuse me for my english, i'm a french user.

---

### Post by Blacktalon on 2007-05-10
Hmm....your scan looks very odd...
What methods have you tried so far?

Also have you tried to do sudo dhclient3 ra0

If not give it a try.  Also go into your network manager and make sure you wireless card is enabled, it might not be and that could be causing the problem, the only reason I suggest this is cause it looks like it knows your card is there but doesn't seem to want to use it.


Hope this will help,
~BT

---

