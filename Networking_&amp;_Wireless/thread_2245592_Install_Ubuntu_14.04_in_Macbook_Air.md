---
title: "Install Ubuntu 14.04 in Macbook Air"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by slamatic on 2014-09-24
I'm trying to install ubuntu 14.04 to my Macbook Air by USB bootable driver, but no wireless connect is detected. I tried to enter "iwconfig" and the output is "no wireless extension".
Could you help me?

---

### Post by Hadaka on 2014-09-24
Hi,please open a terminal..ctrl/alt/t then COPY
and paste the commands one line at a time.
```
rfkill list all
lsmod | egrep 'wl|b43'
lspci -nn | egrep '0200|0280'
sudo su
ls /lib/firmware/b43 | grep ucode15.fw
exit 0
```
please post the output.
thanks.

---

