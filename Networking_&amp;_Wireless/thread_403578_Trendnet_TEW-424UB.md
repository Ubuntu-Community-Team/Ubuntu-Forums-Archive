---
title: "Trendnet TEW-424UB"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by Weird Alexis on 2007-04-07
Hello, I have a USB wireless adapter, model Trendnet TEW-424UB. I'm using egdy on a Dell XPS 210 desktop. I installed the driver in ndiswrapper, and it seems to work:

```
ndiswrapper -l
Installed drivers:
sis163u         driver installed, hardware present
```

One of my problems is that I can't set the ESSID. This is the output of iwconfig:

```
$ iwconfig wlan0
wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          RTS thr:2312 B   Fragment thr:2312 B   
          Power Management:off
          Link Quality:100/100  Signal level:-90 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I set the ESSID with the command:

```
$ sudo iwconfig wlan0 essid XXXXXX
```

There is no output, which I guess means "success". But the ESSID is still off/any...

```
$ iwconfig wlan0
wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          RTS thr:2312 B   Fragment thr:2312 B   
          Power Management:off
          Link Quality:100/100  Signal level:-90 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Has anyone tried this adapter with edgy?

---

