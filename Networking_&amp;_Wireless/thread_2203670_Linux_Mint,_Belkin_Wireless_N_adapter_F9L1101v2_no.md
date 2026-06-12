---
title: "Linux Mint, Belkin Wireless N adapter F9L1101v2 not exceeding G speeds"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by heaver2 on 2014-02-04
Hello guys,

After following this post:

[http://ubuntuforums.org/showthread.php?t=2176114](http://ubuntuforums.org/showthread.php?t=2176114)

I've gotten my Belkin N600 dual band USB adapter to connect to my N600 dual band router on the 5GHz channel.
The only problem is it's capped at 54Mbps!  Both the adapter and the router support 2.4 and 5 GHz, and my phone
can connect to the router at 5 GHz and get connection speed of 100+ Mbps.  Sounds like a driver issue with the adapter.

Some info:

Adapter: Belkin F9L1101v2
Driver: rtl8192du from [here]("https://github.com/lwfinger/rtl8192du")
OS: Latest version of Linux Mint

iwconfig wlan1
```
wlan1     IEEE 802.11an  ESSID:"blah"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.765 GHz  Access Point: blahblah   
          [COLOR=#b22222]Bit Rate:54 Mb/s[/COLOR]   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=99/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo iwlist scan
```
wlan1     Scan completed :
          Cell 01 - Address: blahblah
                    ESSID:"blah blah"
                    Protocol:IEEE 802.11an
                    Mode:Master
                    Frequency:5.765 GHz (Channel 153)
                    Encryption key:on
                    [COLOR=#b22222]Bit Rates:300 Mb/s[/COLOR]
                    <snip>

```
So the network supports the higher bit rate, and we are connected on the 5GHz channel 
with no other devices to drag the speed down, and my phone was
able to get 100+ Mbps speeds.  Any thoughts guys?

EDIT:  Any idea where I would find a configuration file for the driver?  Still pretty ignorant
of how the module system works.

---

### Post by varunendra on 2014-02-06
Hello heaver2, Welcome to the forums ! :)

This driver or support for your card is probably not yet included in the mainstream kernel, so I'm not much hopeful about being able to make it any better. But let's take a look at your overall wifi setup to see if there is something obvious that we can tweak to improve the speed.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

