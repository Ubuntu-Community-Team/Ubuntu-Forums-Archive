---
title: "[Ubuntu] Ethernet connection not visible"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by ubupro97 on 2015-01-23
Ubuntu 14.04 64bit

I have found this appears to be a common issue on 14.04, but none of the help threads helped me.

Ethernet works fine on Windows, does not show up on Linux. A few commands shows that it does detect the hardware, however is not being given an ip address. 

Thanks in advance for your help.

---

### Post by Hadaka on 2015-01-23
hi, please open a terminal ctrl/alt/t then
COPY and paste these commands, one line
at a time..
```
uname -a
lspci -nn | egrep '0200|0280'
rfkill list all
```
post the output
thanks

---

