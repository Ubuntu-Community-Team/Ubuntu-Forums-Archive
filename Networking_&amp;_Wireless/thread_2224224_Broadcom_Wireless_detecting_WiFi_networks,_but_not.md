---
title: "Broadcom Wireless detecting WiFi networks, but not connecting in Ubuntu 13.10"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by Varun_C on 2014-05-15
Command: 

**lspci -nn | grep 0280**


Result:

**02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)**

Please help..

---

### Post by varunendra on 2014-05-15
Hi Varun!

Have you read this sticky thread yet : [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) ?

Essentially, this is all you should need to do -
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot.

If this doesn't solve the problem, please post back a detailed report created by 'wireless_script' as asked in this post : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) (the script mentioned in the post is experimental, but hopefully more info that it provides would be more helpful).

---

### Post by Varun_C on 2014-05-15
Thanks for the reply..

I will try it and post back the result..

---

### Post by Varun_C on 2014-05-17
Thanks . It worked..

thank You very much

---

### Post by varunendra on 2014-05-17
You're welcome. :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Thanks!

---

