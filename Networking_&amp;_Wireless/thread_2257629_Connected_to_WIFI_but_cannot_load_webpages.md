---
title: "Connected to WIFI but cannot load webpages"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by jameshughes1996 on 2014-12-21
I am a total beginner to Ubuntu and Linux in general. I have recently built a pc and put a wireless adapter in so I could connect to the internet wirelessly. I am able to find and connect to my home network with no problems, however when I try to load any web page it does not work. I have seen several threads on this but it doesn't fix my issue, what do I do to connect and load pages properly? Thanks

---

### Post by Hadaka on 2014-12-21
Hi please post the output of..
```
uname -a
cat /etc/issue
lspci -nnk | grep iA3 net
ifconfig
```
thanks.

---

