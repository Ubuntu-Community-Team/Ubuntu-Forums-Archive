---
title: "wifi iwconfig - high &quot;invalid misc&quot;. Should I be worried??"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by linuxa on 2005-11-18
Hi there

So here's my little paranoia of the week. I type in iwconfig, having just configured my wireless network using ndiswrapper for a Linksys WPC54G on a Toshiba laptop, and having been online for about half an hour.


> 
lo no wireless extensions.

eth0 no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0 IEEE 802.11g ESSID:"<blah blah>"
Mode:Managed Frequency:2.412 GHz Access Point: xx : xx : xx : xx : xx : xx
Bit Rate:54 Mb/s Tx-Power:14 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management: off
Link Quality:100/100 Signal level:-45 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:395 Invalid misc:53711 Missed beacon:0

sit0 no wireless extensions.
	

I'm somewhat puzzled by the "Invalid Misc" count, the manual says that it's related to:


> 
Other packets lost in relation with specific wireless operations. 	


My Linux laptop also seems to get a lower priority on the router than the other wireless client (Windows). It gets something like 2~3% of the total downlink bandwidth...

Was just wondering if this is normal behaviour for a wireless card on (K)ubuntu.

Oh, the "Excessive retries" count isn't too comforting either. :(

Any help would be greatly appreciated...

---

