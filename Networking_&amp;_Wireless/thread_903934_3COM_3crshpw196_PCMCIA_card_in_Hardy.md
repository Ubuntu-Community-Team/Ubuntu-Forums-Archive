---
title: "3COM 3crshpw196 PCMCIA card in Hardy?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by gfunkdave on 2008-08-28
For some reason, I can't get this card to work with WPA in Hardy, even though it's listed as a supported card and that WPA is supported in the list of supported cards.

When I connect to a WPA network, it only gives me options of WEP or LEAP encryption in the "enter network key" dialog.

I've tried downloading the Windows drivers from 3com.com and installing them with ndiswrapper, but ndiswrapper complains that the driver is invalid. The sys file IS there. 

I've also tried downloading the atmel driver source but can't get it to compile.

lspci doesn't list the 3com card as present, even though I can use it to connect to non-WPA wireless networks.

My network is configured (using Tomato firmware on a Linksys router) to support WPA or WPA2, and TKIP or AES encryption.

Any ideas? 

Thanks so much...

---

### Post by gfunkdave on 2008-08-31
bump...anyone?

---

