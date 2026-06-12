---
title: "No internet connection wired or wireless"
date: 2014-12-14
forum: Networking &amp; Wireless
---

### Post by bris1124 on 2014-12-14
New to this just installed Ubuntu 14.10 put in all Ethernet info no connection it does see wireless network but will not connect. I have tried sudo apt-get update and sudo apt-get dist-upgrade but because there is no internet connection it will not work I need some help bad.:mad:

---

### Post by Hadaka on 2014-12-14
please post the output of,,

```
lspci -n | egrep '0200|0280' | awk '{print$3}'
lsmod | egrep 'b43|wl'
rfkill list | grep -i yes
```
thanks

---

