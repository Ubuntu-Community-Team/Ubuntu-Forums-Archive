---
title: "Severe wireless issues with Ubuntu 8.10 (Ralink RT2600)"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Berrex on 2008-11-17
Hello. I'm having some serious issues with my wireless connection in Ubuntu that's making the system almost completely unusable. I've done some searching around and it seems that these issues are common with Ralink cards like mine, but the only solutions I can find are for the 25xx cards, and I have a RT2600.

Basically, what's been happening is that my connection speed fluctuates wildly. For maybe 4 or 5 seconds I'd get a the regular transfer rate (between 400 to 600 KB/s), but then it would instantly drop off to 0 KB/s to 30 KB/s and would remain there for a good 30 seconds, one minute, two minutes, five minutes... and then it would jump back up to the standard transfer rate for a couple more seconds. It's been repeating this process over and over again.

I saw a forum post earlier today (sorry, I can't find the link) that suggested running this command in the terminal:
$ sudo iwconfig wlan0 rate 54M

I did that, and it helped a *little*, but the problem is still very much persisting.

In case it's needed, running iwconfig brings the following:
```
wlan0     IEEE 802.11bg  ESSID:"Netgear9856"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:2A:54:58:1A   
          Bit Rate=54 Mb/s   Tx-Power=9 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=79/100  Signal level:-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have a Ralink RT2600 card. Please let me know if you need any further information. A solution would be much appreciated, as I really don't want to have to go out and buy a new NIC.

Thanks.

---

