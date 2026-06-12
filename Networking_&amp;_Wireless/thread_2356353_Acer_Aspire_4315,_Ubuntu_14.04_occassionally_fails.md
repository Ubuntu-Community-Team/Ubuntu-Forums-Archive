---
title: "Acer Aspire 4315, Ubuntu 14.04 occassionally fails to connect to WIFI"
date: 2017-03-22
forum: Networking &amp; Wireless
---

### Post by paranoid.android88 on 2017-03-22
Hi all, first post and I'm a bit of a n00b so go easy on me this time. 

I've installed Ubuntu 14.04 32 bit onto this old Acer Aspire. It all worked fine, installed all the updates etc etc and used it for about a day, then it just failed to connect to my wifi network.

I rebooted, connected and disconnected and turned everything off and on with no luck. Then I was checking to see whether it would (in theory) connect to a FON network, and it would. I switched it back to my usual wifi network and its online again. 

Any idea what's going on? 

All I know of the laptop itself it that the RAM has been upgraded from 512 MB to 2 GB but I believe that's about it. It uses a 802.11b/g WLAN wireless card if that means anything to you. 

Cheers in advance.

---

### Post by praseodym on 2017-03-22
Hi there,

please open a terminal with CTRL+ALT+T and show the outputs of these commands when its not working:
```

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

---

