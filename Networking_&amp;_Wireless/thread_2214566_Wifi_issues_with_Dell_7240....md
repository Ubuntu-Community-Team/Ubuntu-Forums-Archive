---
title: "Wifi issues with Dell 7240..."
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by Karl_J on 2014-04-02
This is about wireless, but I thought I'd also note my experiences putting Ubuntu onto a current Dell Ultrabook e7240.  Hopefully this is helpful for anyone else using (searching?) for Ubuntu WiFi issues on the 7420.  Skip to the last paragraph if you want the quick answer.

So I've had my Dell 7240 for alm40 for almost a month.  Once I got it I wiped the SSD and installed Ubuntu 12.04.4 LTS (downloaded from Ubuntu because I read lots of bad results with Dell's 12.04.2).  Anyhow, this was a plain disaster.  The system was slow, various apps would crash, not to mention WiFi issues.  So within 48h of installing 12.04, I wiped my drive and installed Ubuntu 13.10.  

The first thing I will say was 13.10 was at the very least stable.  My random crashing issue was fixed.  However, my WiFi was very spotty.  For example, my range was extremely limited.  If I was like 20 feet from my AP, the connection would just randomly drop.  No amount of WiFi changes seemed to help.  I have an ASUS RT-AC66U, configured in "Access Point" mode.  If I stayed 5 feet from the AP, it seemed to work.

The other odd issue I found was the WiFi signal strength would go down one bar at a time, with both me and my AP at fixed locations until it would finally drop. Again, changing channels, repositioning made no difference.  Both issues were on the 2.4Ghz network.  For 5Ghz networking no traffic could be sent/received regardless of distance from my AP.  I could authenticate to the WiFi, connect, but not be able to surf or connect to any other machines on my network.
 
 Since all these issues were only experienced on my Dell e7240 (with the Intel 7260 (rev 73) Dual Band Wireless-AC) I looked at my 4 year old HP 210 Mini Netbook.  It had no issues on my WiFi whatsoever.  It was sporting an a Broadcom BCM4312 802.11b/g LP-PHY (rev 01) WiFi adapter.  My old Dell D620 (which also was working fine on my WiFi network) had a Broadcom BCM4311 802.11a/b/g (rev 01).  The key to note between these two adapters is the 4312 in my Netbook was also a Bluetooth adapter, while the 4311 in my D620 was WiFi only.
 
 I decided to try the BCM4312 in my Dell e7240.  Bluetooth worked instantly, but I had to reinstall my network drivers (according to this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) to get WiFi to work again.  So far so good.  WiFi is stable.  Only caveat I can find is the WiFi switch on the e7240 doesn't work anymore, but that's not a big issue for me.
 
 Hope this is useful,

 KJ

---

### Post by Karl_J on 2014-04-02
Thought I would add that the Broadcom BCM4312 is a WiFi 802.11b/g + Bluetooth 2.1 card.  I looked on eBay and bought the Broadcom BCM4313 WiFi 802.11b/g/n + Bluetooth 4.0 for about $12.  This is closer in specs to the Intel 7260 that came stock with the Dell e7240.  Once I get the BCM4313 I'll repost on how well that card works in the Latitude.

KJ

---

