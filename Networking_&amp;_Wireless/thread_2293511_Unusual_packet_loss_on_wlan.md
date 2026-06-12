---
title: "Unusual packet loss on wlan"
date: 2015-09-05
forum: Networking &amp; Wireless
---

### Post by Kenneth_Hanley on 2015-09-05
Hi guys,

I've got a strange issue with my laptop... I'm running 14.04 on my macbook pro 8,1 using b43 wireless driver. I've posted in networking as I don't believe the issue is apple related... (I could be very wrong!)

I have my home router assigning a static IP to my laptop by way of MAC address. This was working perfectly well until recently (no idea what triggered this) when I started getting some serious packet loss (60-100%) when pinging the router, which is about 1m in front of me! I've been through hell and back trying to diagnose the issue with zero luck... Until last night when I reverted back to a dynamic IP address. Now everything is working beautifully! I used nm to assign my old IP to my wireless connection again and all is still well. 

I was just wondering, does anyone have any clue what could be going on here..?

I've verified that the issue is not with my router as I've applied another static DHCP address to another device (using it's MAC) and pinged the router with zero losses. So I can only imagine the problem is with my laptop. I've attached a pastebin of a wireless-info script below

[http://pastebin.com/S8c2sr82](http://pastebin.com/S8c2sr82)

Any help is much appreciated!

Thanks!

---

