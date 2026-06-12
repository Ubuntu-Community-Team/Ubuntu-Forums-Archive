---
title: "Cannot install STA Broadcom Wireless driver on Ubuntu 12.04"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by dloeb91 on 2013-11-05
Hi, I am a completely new Ubuntu user, running 12.04 on a Dell Inspiron 1545.  I am getting a failed installation message when I try to activate the Broadcom STA wireless driver.  I have searched around and found threads from others with the same issue, but the solutions always involve a "sudo apt-get" command.  When I type in commands with "sudo," it asks me for a password.  When I try to then type a password, I am unable to type anything.  Can anybody help me with this issue?

---

### Post by Hadaka on 2013-11-05
Hi,please open a terminal...ctrl/alt/t then
COPY and paste these comnds..
```
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
```
post the output..
*you will not see your password when it its entered
it will be invisable..thats normal.
thanks.

---

