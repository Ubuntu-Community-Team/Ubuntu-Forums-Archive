---
title: "how I resolved wifi interface not getting IP on boot (ralink)"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by wayover13 on 2008-04-14
Added a ralink PCI wifi card to my Mythbuntu system recently. This card uses the rt61pci module. It was accurately detected and proper modules loaded, but for some reason it would not initialize (i.e., would not obtain an IP from my wifi router) on boot-up. I tried setting up the card through XFCE's network manager, but it still would not initialize on boot. If I would run ```
ifup wlan0
``` from the command line after the system had booted, the system would obtain an IP just fine. Not sure why the card would not simply initialize on boot.

Anyway, I did some googling and was able to resolve the problem using bits and pieces of information posted on this and other help forums. My solution was as follows. I edited the /etc/rc.local file, adding the line ```
ifup --force wlan0
``` before the line ```
exit 0
``` in that file. Caveat: I'm not sure the --force option is needed, but it seemed like it couldn't hurt anything. Once I rebooted, wlan0 got its IP from my router and I was ready to network with the Mythbuntu machine.

Hope this may be of help to someone else.

James

---

