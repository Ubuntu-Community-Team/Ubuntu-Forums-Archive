---
title: "Cannot find my wireless"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2008-09-30
Hello, I have just installed Ubuntu Hardy on a desktop PC. I like it so far. Even compiz works on an ATI card. But I cannot connect to my wireless network. I have tried Network Manager and wicd. Neither will detect my wireless network.

Ubuntu detects two network devices;
Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91) 
Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

But iwconfig shows this;
user1@user1-desktop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 

Shouldn't I see wlan0 somewhere? What is wrong?

---

### Post by oldsoundguy on 2008-09-30
You aren't the only one with problems with Realtec wireless:
[http://www.google.com/search?q=install+realtek+8185+in+hardy&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=install+realtek+8185+in+hardy&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Broadcom is another that causes issues.

---

