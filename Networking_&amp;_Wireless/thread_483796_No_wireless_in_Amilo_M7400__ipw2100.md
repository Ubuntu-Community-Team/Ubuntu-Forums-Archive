---
title: "No wireless in Amilo M7400 / ipw2100"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Camulus on 2007-06-25
Hi to all, this is my first post.
I work with ubunto fron some time ago, but use a ethernet connection to Internet because I have not a wifi router. Now I have it, but I cant connect. 
I have a Fujitsu Siemens Amilo M7400, with Ubuntu 7.04 and Windows XP Home. With WinXP it works perfectly: button actives wifi, led is on, connect is possible. So, the router is OK. Come to linux...
Detection of card is ok:
```
camulus@LBL:~$ dmesg | grep ipw
[17179615.932000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[17179615.932000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[17179615.932000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
```
Modules seems OK too:
```
ieee80211              33608  1 ipw2100
ieee80211_crypt         6016  2 ieee80211_crypt_wep,ieee80211
```
So let's go, but...
```
camulus@LBL:~/linux/fsam7400-0.5.1$ iwconfig
...
eth1      unassociated  ESSID:"XXXXXXXX"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

unassociated??? What? I've lloked for a lot of forums, but everyone have problems AFTER this step. I don't know how to continue. Can anybody help me? Ah! The button don't work BUT the led is always flashing (so there's no problem in hardware, isn't?)

Thanks!

---

### Post by timohnani on 2007-08-02
Hi Camulus,

It should be quite simple to solve your problem. Essentially the FSAM7400 module has not been loaded. All you have to do is startup this module. 

Alternatively you can follow the instructions here: 

[http://ubuntuforums.org/showthread.php?t=189540&page=7](http://ubuntuforums.org/showthread.php?t=189540&page=7) 

read post #61. 

This way your wlan will load by default when you startup.

Hope this helps. 

Timo

---

