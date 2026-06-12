---
title: "Old Laptop Wifi"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by ldc2357 on 2016-11-06
So I am trying to get the wifi to work on my old laptop. When I say old, it has a single core processor and I bought it in the summer of 2005. The wifi can be turned on and off manually, the button lights up blue when its working. I was running Puppy linux earlier from a cd and it worked fine, but I have Lubuntu on here that I want to use. Even though the appropriate drivers are installed, it just does not want to work.

Where do I start? The additional drivers has two entries that say Unknown, I assume one is the modem and the other is the graphics card. I have a Compaq Presario M2105.

---

### Post by Hadaka on 2016-11-06
Hi please open a terminal...Ctrl/Alt/t.. and do..
```
cat /sys/class/dmi/id/sys_vendor
cat /sys/class/dmi/id/bios_date
lspci -n | awk '/0280/{print$3}'
```
Post the output...thanks

---

