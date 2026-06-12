---
title: "beginner's wireless/cable question"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by ginestre on 2007-05-28
Please forgive what may be a very foolish question. 

I have feisty on my pc attached by cable to a netgear wireless/cable router, and can from my PC see all of the other windows PCs that are connected by cable. I can read shared disks etc- which is what I want. But the only windows PC that is connected to the router via wireless is completely  invisible to me. 
 
Is that just because I don't yet know how to configure things properly, or are wireless connections inherently different from cable? Will I be able, with study and help, to connect to the wireless PC in the same way as to the cabled?

Thanks.

---

### Post by mkor on 2007-05-28
Yes, you should be able to set it up so that both computers see each other. There is no difference between these two connections on TCP/IP protocol level, so they will be treated the same way by programs.

It would help if you posted here results of ifconfig from your linux box and ipconfig from your windows box. Can you at least ping the windows from linux? Are they in the same network, or do you have two different networks for cable and wifi?

---

