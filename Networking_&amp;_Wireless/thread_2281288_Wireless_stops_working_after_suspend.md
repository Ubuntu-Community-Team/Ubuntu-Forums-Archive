---
title: "Wireless stops working after suspend"
date: 2015-06-05
forum: Networking &amp; Wireless
---

### Post by daniel280 on 2015-06-05
I've recently installed Ubuntu as a dual boot on my new HP laptop. Whenever I close the lid or suspend it the wifi disconnects. If I click on the network thingy in the top left it says "wireless disabled by hardware switch". I can't find a switch anywhere on the case, and even if it was a hardware switch wouldn't it always be off, not just after a suspend? 

I looked around a bit already and tried running ```
rfkill list all
``` 
Which outputted 
```
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
```

Not sure if that's actually useful though..

---

