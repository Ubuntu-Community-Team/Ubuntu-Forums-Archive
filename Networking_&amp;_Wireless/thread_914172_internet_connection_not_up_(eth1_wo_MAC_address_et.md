---
title: "internet connection not up (eth1 w/o MAC address eth1:avahi with MAC address)"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by yty on 2008-09-08
Hi,
I am a newbie in Linux and have being searching solution to connect internet for some weeks.

Hereafter summary of investigations 
1- OS/PC : Ubuntu 8.04 Hardy Heron/PC motherboardK7S5A+512MB
2- lspci : lan board is well recognized
3- admin/network tools -> eth1 shown without information viz no IP,no MAC address, nothing at all
4- configuration of eth1 : result is "this interface doesn't exist"
5- admin/networks tools -> eth1 shown with IPv4, IP address,MAC address , multicast enabled , MTU:1500 , link speed : not available , state : active (all statistic data set to 0).
6- configuration of eth1:avahi : result is "this interface doesn't exist"

Could you please advise for solving this issue ?

Many thanks in advance.

---

### Post by p_quarles on 2008-09-08
Moved to Networking & Wireless. Forums Feedback & Help is for questions about the forums only.

Please post the output of this terminal command:
```
/sbin/ifconfig -a
```

---

