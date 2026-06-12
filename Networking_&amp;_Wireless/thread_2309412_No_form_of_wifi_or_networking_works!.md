---
title: "No form of wifi or networking works!"
date: 2016-01-10
forum: Networking &amp; Wireless
---

### Post by rowenandrubberman on 2016-01-10
So I got ubuntu the other day and everything offline was fine. I wanted to start downloading and going online but had no connection. So I plugged my usb wifi thing in and tryed to set it up and that didn't work. I tryed to look for drivers and found none. I then went and tryed loads of things in the terminal none getting me connected. So it got so annoying I plugged my pc directly into my router and still I can't get anything online to work.

If ANYONE knows how to simply get online or get wifi or get network drivers please help!

Thank you in advance

---

### Post by wildmanne39 on 2016-01-10
Hi, copy and paste the following commands into the terminal one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

