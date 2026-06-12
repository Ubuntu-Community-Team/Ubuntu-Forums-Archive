---
title: "Fatal..."
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by knutaldrin on 2006-08-26
Hey!

I recently installed Ubuntu on my laptop (Medion SIM2000), just because I was pissed off on windoze. 

It woked great, just like my desktop, and I decided I was gonna compile a new kernel. 
I compiled the 2.6.17.9, and it worked great. 

The problem is, my card won't show up in the network manager. 
It did before, and I thought the card was a ZCom XG60x, like in the product listing. That was pure bullshit from Medion. 
I found out it was a Texas Instruments ACX 111 card, and I found a fix why it showed up, but did not work. Anyway, when I now copied the firmware drivers /lib/firmware/2.6.15.*/acx to /lib/firmware/`uname -r`/acx, and make a correct link on the default to 1.2 firmware, and load modprobe acx, it complains "FATAL: Module acx not found!". 

WTF? Anyone have a fix to this? something I made wrong in my kernel?

---

