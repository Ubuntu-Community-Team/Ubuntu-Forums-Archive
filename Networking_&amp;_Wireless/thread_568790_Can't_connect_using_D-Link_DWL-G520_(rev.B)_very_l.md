---
title: "Can't connect using D-Link DWL-G520 (rev.B) very low signal"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by Hamoo on 2007-10-06
[B]Hi,
my D-Link AirPlus DWL-G520 Wireless PCI Adapter(rev.B) gives a very low signal around 20 to 30%, im using Ubuntu 7.04
neither NetworkManager nor Wicd was able to connect i tried them both also i've installed ndiswrapper and disabled madwifi driver the same thing happened no changes the signal is still low while under windows i get 4 bars and connect easily
this morning i tried removing madwifi and installing the last release by compiling it from source but with no luck the signal is still low
i tried everything i know so please if anyone can help i'll be really thankful [/B]

```
ath0      IEEE 802.11g  ESSID:"dijlh"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-61 dBm  Noise level=-92 dBm
          Rx invalid nwid:3389  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by argusBR on 2007-11-28
I have a similar problem here: low signal with Ubuntu (and strong with Windows). I don't lose the connection, but after some 2 minutes, I can't connect to anything. If I restart the network

```
sudo /etc/init.d/networking restart
```

I can get more two minutes of connection.

It seems that the problem is not with the router, as a Windows notebook works without problems.

---

