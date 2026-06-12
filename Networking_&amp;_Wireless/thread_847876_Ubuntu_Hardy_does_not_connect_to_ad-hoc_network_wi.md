---
title: "Ubuntu Hardy does not connect to ad-hoc network with pocketpc"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by fhteagle on 2008-07-03
My Toshiba A105-S4384 laptop ad-hoc's nicely to my AT&T Tilt in Windows XP, but fails to associate correctly under Ubuntu Hardy. I have ad-hoc networked the Toshiba to other devices before, and to this Tilt and a previous 8525 I used before (but very low percentage connection success, and probably never since Gutsy->Hardy upgrade). Wireless card in the Toshiba is an Intel 3945ABG as given by lspci:

```
lspci | grep 3945
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02
```

iwlist finds the ad-hoc network correctly:
```
sudo iwlist eth1 scanning
eth1      Scan completed :

          Cell 04 - Address: 02:18:41:yy:yy:yy
                    ESSID:"WMWifiRouter"
                    Mode:Ad-Hoc
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=93/100  Signal level=-36 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000000bfee4c
```


There are other wireless networks in the vicinity that are trying to use channel 11, but very weak signal -79db signal over -122db noise. Cannot figure out how to force the Tilt to use a different channel, despite searching like crazy for this.

I use nm-applet or iwconfig eth1 essid WMWifiRouter to attempt to select the ad-hoc network, then I get:

```
iwconfig eth1
eth1      IEEE 802.11g  ESSID:"WMWifiRouter"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
And stays that way until networkmanager gives up and heads to another network.

The Tilt shows its MAC to be 00-18-41-xx-xx-xx (hidden for security) and BSSID to be 02-18-41-yy-yy-yy  (matches iwlist eth1 scanning output)

I saw avahi was a problem for some other people so I have removed those packages, rebooted, and see no avahi threads in system monitor.

Using Ubuntu to try to start a new ad-hoc network via iwconfig or networkmanager also fails, as the Tilt does not see the new network whether settings for it are put in to the wireless networks list on the Tilt or not.

So yeah, what now to try and get this to associate correctly?

---

### Post by bimmerd00d on 2008-07-10
In for the solution to this too.  I'd love to get this working on my Tilt.  Have you changed your ROM yet?  that thing has so much more potential than the ROM it ships with.

Have a look here, im a member over there.

[http://forum.xda-developers.com/forumdisplay.php?f=378](http://forum.xda-developers.com/forumdisplay.php?f=378)

---

