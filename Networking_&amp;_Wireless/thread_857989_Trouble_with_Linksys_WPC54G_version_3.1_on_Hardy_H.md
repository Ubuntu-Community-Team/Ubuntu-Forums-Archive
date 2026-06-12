---
title: "Trouble with Linksys WPC54G version 3.1 on Hardy Heron"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by randallecook on 2008-07-13
I have an old laptop on which I want to run Ubuntu. Since it is old, I have to use a PCMCIA card. I bought a Linksys WPC54G since it is popular and matched my WRT54G wireless base station. I believe the card has the Broadcom 4318 chipset. When I opened the package, it turned out to be version 3.1 of the device.

Unfortunately, I have not been able to get the device to work. The lspci command sees it, dmesg says it isn't working (but doesn't say why), ifconfig sees it and says it is up, but the link light on the card never lights and there is no connectivity.

I have tried ndiswrapper, b43-fwcutter, and other approaches I have seen suggested online, but none have worked. It is possible that I have not executed those approaches correctly, but as is typical with howtos there is little information about what to do to confirm success or failure at each major step. I am ready to return the card, but I thought I would turn to the community to see if there are any other suggestions.

Admittedly, this particular revision is not listed as being supported by Ubuntu and Linux on various hardware compatibility sites, but it is not listed as being unsupported either. I want to think that it can work, but it is not looking good. Any last suggestions? Thanks in advance.

Randall

---

### Post by Waklevören on 2008-07-23
Hi, I dunno if I'm too late, You said you tried the b43-fwcutter way, did you do this manually or by hitting sudo apt-get install b43-fwcutter?

---

