---
title: "monitor dlink dwl-g520"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by shunklord on 2007-06-11
Hi!

How to enable monitor mode on this wifi card with ubuntu ? 
With backtrack this work :)

---

### Post by qmxc on 2008-05-19
I have the same wireless card, and i do following steps:

$ sudo wlanconfig ath0 destroy

$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor

This commands activate new interface **ath1** and wifi0 :confused:

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ppp0      no wireless extensions.

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device

After:
$ sudo ifconfig ath1 up

still i can't receive any packets from interface ath1 and wifi0 in wireshark or others... 
In backtrack i haven't any problems with this commands and receiving packets. Why doesn't work in Ubuntu? I need some specific additional software installed in my system?  Thanks for help and sorry for my English

---

