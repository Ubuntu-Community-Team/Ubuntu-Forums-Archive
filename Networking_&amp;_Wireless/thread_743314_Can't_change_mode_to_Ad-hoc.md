---
title: "Can't change mode to Ad-hoc"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-04-02
I just bought Canyon WF-511 Turbo, wireless card. Now I want to connect my laptop to my PC with that card. I read that I need to change mode to Ad-hoc.
Trying doing it like this:
```
 sudo iwconfig wlan0 mode ad-hoc
```
results in
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
```
Here is some information:
```
 wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I tried restarting the comp, but the same thing.

---

