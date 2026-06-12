---
title: "Firmware? Need a Wireless Connection"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by mike76 on 2006-08-20
I read somewhere that maybe one needs to download some "firmware" for their wireless card?  I have plugged in my wireless card and hoped it would just work - it didn't.   Please - How am I going to get a wireless connection working? 

I have a D-Linkk DWL-AG660 plugged into the side of my laptop and the lights just blinks back and forth from ACCT to Link.

---

### Post by runokiab on 2006-08-20
As you can see on [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link) your card should have an Atheros chipset (depending on the hardware revision). If you have such a revision your card is supported by the madwifi driver, which you can get from [http://madwifi.org/](http://madwifi.org/)

---

### Post by shieldfire on 2006-11-18
Sorry for replying to an old post, but I was looking to solve the problem in my post.

I changed to this from a Netgear WG511U card.
This one works "out of the box" with Edgy, while there were serious problems with Dapper. It is slightly unstable though, losing contact with the AP from time to time for no apparent reason. ifdown/ifup has solved the problems so far.

---

