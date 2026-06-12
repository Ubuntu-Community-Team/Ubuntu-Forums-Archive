---
title: "how to auto transfer between DHCP and Static IP"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by xmzhu on 2007-11-09
[I]Hi
There is a problem. I installed ubuntu 7.04 on my laptop.
On daytime, I take it to office and set it to static ip address (no DHCP for me). After work, I take it home and set it to DHCP. In order to make it easier, I write a script like following;

import string,os
print "Only Root can execute the script!"
place = input("put the place(0 for Home or 1 for Work):")
if place == 0:
   os.system("cp /etc/network/interfaces_home /etc/network/interfaces")
   os.system("/etc/init.d/networking restart")
   os.system("cp /etc/resolv_home.conf /etc/network/resolv.conf")
   os.system("host cyberciti.biz")
   print "Done"
if place == 1 :
   os.system("cp /etc/network/interfaces_work /etc/network/interfaces")
   os.system("/etc/init.d/networking restart")
   os.system("cp /etc/resolv_work.conf /etc/network/resolv.conf")
   os.system("host cyberciti.biz")
   print "Done"

[/I]

The problem is , only by rebooting can it connect to network after executing script. I think it should not be designed like this.  In fact, after execution, it can ping  router . But it can not log on internet.

Why?
Thank you

---

### Post by Peter09 on 2007-11-10
There is a significant problem with DHCP in Ubuntu, you could be seeing some of these problems. Can you ping any ip addresses but not connect by name? Also, make sure that DNS names are being resolved otherwise you will not be able to get an external web page.

---

### Post by xmzhu on 2007-11-12
> **Peter09 said:**
> There is a significant problem with DHCP in Ubuntu, you could be seeing some of these problems. Can you ping any ip addresses but not connect by name? Also, make sure that DNS names are being resolved otherwise you will not be able to get an external web page.
 I can ping the dns sever, gateway ,but cannot connect by name

---

