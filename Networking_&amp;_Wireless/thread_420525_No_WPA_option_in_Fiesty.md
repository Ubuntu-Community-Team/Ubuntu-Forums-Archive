---
title: "No WPA option in Fiesty?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by yetanothername on 2007-04-23
Hi,

I recently set up my wifi and was happy to see the fiesty can detect it with no problems. On good advice from user Catsworth I set up the router for WPA encryption.

The problem is when I go to Network Setting and click on the properties for the wifi connection I only have a choice of WEP (ascii of hex). There is no WPA in the drop down listing. 

Am I missing something or is WPA not available in Fiesty? 

Any help would be appreciated.

cheers

---

### Post by x64Jimbo on 2007-04-23
Is your card a broadcom by any chance? if so, that may be the problem. IIRC, the kernel module bcm43xx does not support WPA yet. You may want to look into using Ndiswrapper with your card for better support of its features.

---

