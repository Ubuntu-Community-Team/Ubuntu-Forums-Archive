---
title: "Atheros monitor mode no traffic"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by thevoidreturns on 2008-04-21
Hello,
      I'm going crackers with this one. Basically, I am trying to put my Atheros card into Monitor Mode in which I succeed. No problems there. My issue is that when I start Airodump-ng or Kismet I am receiving no monitor mode traffic at all!

Previously, I have had this working before my reinstall of Ubuntu and everything worked fine.

I have downloaded through apt-get the madwifi-tools, aircrack-ng, and also kismet (through Add/Remove programs). 

Please can someone point me in a direction of how to solve this problem?

Thanks
Adam

---

### Post by thevoidreturns on 2008-04-21
Took most of the day to figure out what the problem was, well I didn't find out what the problem was but anyway I got a solution to my problem:

I had the madwifi driver 0.9.3.2 installed, I downloaded 0.9.4 from their website and compiled and installed that. Everything is working ok now.

[http://www.madwifi.org](http://www.madwifi.org)

For future reference I am using an Atheros 5005G I think.

---

