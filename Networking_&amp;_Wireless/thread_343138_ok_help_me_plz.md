---
title: "ok help me plz"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by lllooonnniiieee on 2007-01-21
ok i got ubuntu up and running now i need help to install stuff like my wifi driver i got the linux driver from the website (gigafast.com) then i put it on my flash drive and reboot load up ubuntu instead of windows(dual boot 2 partitions) then i open the flash drive and find the Archive and then i get lost i have had ubuntu for 5 days and cant do anything cause i have no internet on it so plz help me

---

### Post by mssever on 2007-01-21
In general, Windows drivers don't work on Linux. What wireless card do you have (specific model)? You can type ```
lshw -class network | less
``` in a terminal window to find out.

Next, search the forums for your wireless model and/or the brand. Failing that, search the forums for NDISWrapper (the sometimes exception to the rule about Windows drivers not working on Linux).

If you post the above info here, maybe someone can help you.

---

