---
title: "wifi connected but no internet"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by saviokarim04 on 2014-01-03
Hello guys I am new to Ubuntu and I just updated from 13.04 to 13.10. But I am having this problem where I can't access the internet even though it shows that the WiFi is connected. I have gone through a lot of forums but I still haven't been able to find a solution. Any help would be appreciated. Thanks.

P.S. I know I have to post a lot of results from the terminal but I don't know which all :)

---

### Post by praseodym on 2014-01-03
Please show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work? What computer is it?

---

