---
title: "Dial-Up Connection Woes..."
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by Alex4R on 2005-04-10
Well, I finally got an external serial modem. I am using ppp to connect. The modem will dial, and you can hear it squealing like it is connecting, and then theres silence for about 10-15 seconds and you can hear the modem disconnect. At first I thought maybe I got my username/password incorrect, because it is LONG (I use RASspy.exe to work around NetZero's software). So I copy it directly into notepad and open it in Ubuntu and it is correct. Next, I thought maybe the DNS settings should be set to dynamic rather than static, so I changed that. No luck. Then after some more research, I found that people couldn't connect unless they disabled their network, so I disabled network eth0. Still nothing. Then I found that someone had used CHAP authentication rather than PAP, which is what it was set on. So I changed that and STILL no luck!

Anyone have any suggestions? They would be greatly appreciated!!

---

### Post by Alex4R on 2005-04-10
UPDATE: I found DNS server information for netzero, found [here](http://www.geocities.com/daveinfopage/palmpilot_freeISP.html), and attempted to set the nameserver to static in pppconfig. No luck here...

---

### Post by Alex4R on 2005-04-13
Anyone?

This is my error in the logfile:

[color=red]LCP: Timeout sending config requests[/color]

---

