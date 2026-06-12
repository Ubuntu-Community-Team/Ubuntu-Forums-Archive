---
title: "laptop connected to router but no internet access"
date: 2017-01-27
forum: Networking &amp; Wireless
---

### Post by shown440 on 2017-01-27
My ubuntu(16.04.1 lts) laptop connected to the wifi router. Everything is ok. But I can't access internet. Every time it shows that server not found.
For my wired connection, I have same problem. 
Please suggest me as early as possible...

---

### Post by wildmanne39 on 2017-01-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

