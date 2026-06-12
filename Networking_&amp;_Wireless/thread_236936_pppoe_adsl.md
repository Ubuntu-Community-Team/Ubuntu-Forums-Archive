---
title: "pppoe adsl"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by RoyalShrubber on 2006-08-15
Hi

I have problem connecting internet. It worked in the past on the same hardware, but then I removed Ubuntu. Now I have returned but I can't connect back. (I assume there isn&#8217;t any significant change between the old 6.06 and my new 6.06.1 version)

I am connecting trough wireless to pppoe ADSL. I use SMC SMCWPCI-G which is supported trough Madwifi, and I use rp-pppoe client. I also use WEP encryption. Rp-pppoe client connects to ADSL modem (apparently), but still I can't use FF or anything else.

See picture
[[img]http://www3.shrani.si/thumbs/screensh821657.png[/img]](http://www3.shrani.si/o.php?screensh821657.png)

I don't know what this exactly means, but it looks like I can only upload... 

Thanks for help

---

### Post by Rhaurison Bergamin on 2006-08-16
Try look for log messages from pppd and use tcpdump to see what is happening.

---

