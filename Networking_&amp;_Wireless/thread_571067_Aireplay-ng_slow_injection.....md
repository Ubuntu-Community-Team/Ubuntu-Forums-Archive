---
title: "Aireplay-ng slow injection...."
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by giant22000 on 2007-10-08
Hi... i'm using Ubuntu 7.04 fiesty fawn and aircrack-ng v0.9.2 and have successfully used aireplay-ng with my proxim orinoco 8470-wd.  The problem i'm having is when I first used aireplay to inject packets I just used the -3 option to capture an arp-request from an already associated client.  When replay kicked in and started injecting these packets, it was only generating 10-15 new data per second.  Due to my own ignorance, I didn't think anything of it and just thought that was the norm...  After a while, I wanted to further my knowledge about injecting packets, so I started playing around with chopchop/fragmentation.  After my first successful packet generated with chopchop/fragmentation, I proceeded to inject, "aireplay-ng -2 -r arp-packet.cap ath0".  Wow, what a difference I got, new data was being generated at about approx. 350 per second.  I used this method a few more times and then the problems started.  It started generating data at 250 per second, then 150 per second, then 30 per second. Now it will not generate data at rate more than 30 per second despite the fact that i'm sending approx. 350-375 pps.  Has anybody ever experienced this/heard of this before??  Also, when I capture an arp-request and replay this, it only generates data at about 10-15 new data per second.  Any suggestions??  Thanks for any help!

---

