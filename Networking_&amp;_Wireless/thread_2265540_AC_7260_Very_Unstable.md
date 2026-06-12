---
title: "AC 7260 Very Unstable"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by richard103 on 2015-02-16
I'm sure you have encountered many users with this problem before but nothing beforehand could solve my problem as the issue has popped up again. I have tried disabling wireless N and also turned power management off. I have tried all firmware versions from ucode 7 to 10 but nothing has helped. Any help would be appreciated, my current download speed is 4mb/s while on windows I could manage 15mb/s. 

Here are my results for the wireless script:
[http://paste.ubuntu.com/10251670/](http://paste.ubuntu.com/10251670/)

---

### Post by jeremy31 on 2015-02-16
Try ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` and change ```
options iwlwifi 11n_disable=1
``` to ```
options iwlwifi 11n_disable=8
``` and reboot as this should give your speed a boost

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)

---

