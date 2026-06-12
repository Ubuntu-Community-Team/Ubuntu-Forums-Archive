---
title: "Internet connection issue. VPN only?"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by outkast3001 on 2014-05-01
Ubuntu 14.04 (64bit),
Acer 5742 Laptop,
3GB RAM, 250GB HDD and Intel Core i3,
Qualcomm Atheros AR9287 Wireless Network Adapter,
Netlink BCM57780 Gigabit Ethernet PCIe,
Ironlake mobile graphics.


Unable to connect to internet through using Firefox, Thunderbird, apt-get or Synaptic. If I Start my VPN service I can use all these no problem. Although it is a bit inconvenient. 

This is a near fresh install of the Trusty and I have not modified the firewall. Up till last night before I went to bed all was good. My Tower with Ubuntu 12.04 is running with no issues, as is my phone. I have reset router and tried Ethernet connection with same outcome. 

Network manager is not displaying a driver in connection information. Which is the only thing I can make out to be wrong I think. I have included my wireless info also.
[ATTACH]252712[/ATTACH]

Hopefully that worked.

Anyway I am hoping someone can help me out to get my computer accessing the internet again without the need to always be using my VPN. Thank you for taking the time to read this. Any missed needed information I can supply happily. Thanks again.

Edit: Since posting I have tried an older Kernel 3.8? No effect. Blacklisted the drivers for my wifi (ath9k), no effect. I have since gotten Windows 7 within my Virtualbox to connect to the internet but still no joy with the main operating system even though I can ping various websites. I even tried to build a Kernel but quickly got a bit out of my depth. I tried tweaking within Firefox, tweaking my router, playing around with the Network Manager and I have exhausted Google, Duck, yahoo and Bing and am slowly running out of ideas. Any input would be appreciated?

---

### Post by varunendra on 2014-05-04
Welcome to the forums outkast3001 !

If you are still having the same problem, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
route -n
nm-tool
```
..from both when the VPN is started and when it is not.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

