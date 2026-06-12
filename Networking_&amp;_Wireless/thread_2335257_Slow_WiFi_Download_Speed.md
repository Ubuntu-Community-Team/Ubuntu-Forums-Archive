---
title: "Slow WiFi Download Speed"
date: 2016-08-26
forum: Networking &amp; Wireless
---

### Post by prosmart on 2016-08-26
Greetings

I have a mixed network around my place.

Fibre to the premises connected to a TP-Link N750 running OpenWRT.

From the router:

[COLOR=#404040][FONT=&amp]Model: TP-Link TL-WDR4300 v1
F/W: [/FONT][/COLOR][COLOR=#404040][FONT=&amp]OpenWrt Barrier Breaker 14.07 / LuCI Trunk (0.12+svn-r10530)

[/FONT][/COLOR][COLOR=#404040][FONT=&amp]I have a couple of hardwired connections from the router and the rest of the devices in the house are wireless.

The problem is with my Mythbuntu server which is a lot slower than it should be when downloading to it (externally or across the LAN).

Tried running speedtest-cli and got this result:

[/FONT][/COLOR]```
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from iiNet (59.167.212.97)...
Selecting best server based on latency...
Hosted by AARNet (Brisbane) [16.69 km]: 4.755 ms
Testing download speed........................................
Download: 16.09 Mbit/s
Testing upload speed..................................................
Upload: 16.57 Mbit/s

```

[COLOR=#404040][FONT=&amp]In contrast here are the results from my Dell Latitude connected by WiFi to the same router.

[/FONT][/COLOR]```
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from iiNet (203.206.187.150)...
Selecting best server based on latency...
Hosted by Telstra (Brisbane) [29.25 km]: 6.854 ms
Testing download speed........................................
Download: 38.12 Mbit/s
Testing upload speed..................................................
Upload: 17.07 Mbit/s

```

I've also confirmed the issue using iperf and Filezilla back and forth and got similar results each time.

Can anyone who understands this area better than I (not a very big ask) take a look at the attached wireless-info and perhaps offer some advice? 

I would be very grateful if I could solve this and save me running cables around the place in a renter.

Thanks and Regards

Nigel.

---

### Post by kurt18947 on 2016-08-27
I had a similar problem with wifi speeds. I have a Thinkpad with Intel 6200 card. Using the 2.4 Ghz. band I could never get over 52-58 mb./sec after trying every Intel fix I could find. After acquiring a Netgear router that supported 2.5 Ghz. & 5 Ghz. and installing DD-WRT, the 5 Ghz. band gives me around 100 mb./sec. per iwconfig. Speed tests say around 50 - 60 mb./sec. The cost is less range with 5 Ghz. but that's not necessarily a bad thing in cluttered wifi environments.

---

