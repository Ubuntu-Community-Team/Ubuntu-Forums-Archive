---
title: "[SOLVED] Vista/Ubuntu Wireless Adapter Problem"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by cheesypoof on 2008-09-10
Alright, let me start this off by saying I only began to experience this problem after I received an update for Ubuntu. I don't use my Ubuntu very often, I mostly use Vista. First of all, the wireless internet worked just fine on my Vista before this Ubuntu update. It seems to me every time I boot Ubuntu, it resets the device's settings on Vista. Vista thinks it is a actually a new device and starts installing drivers. Also, I have noticed when I connect to my wireless network, both operating systems use different mac address. This was not the case before the update. By the way, the network device is an RTL8187 and I have a dual boot. In addition, I noticed a new message that I believe relates to this in the boot that I will log on my next startup. Please help me figure out what is going on here. If you want me to post any information to help you, let me know. Thanks in advance.

---

### Post by cheesypoof on 2008-09-10
Actually I think I have narrowed it down to this bug([https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/258344]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/258344")). I reverted back to 2.6.24-20 and it seemed to have fixed my problem. Thanks anyways.

---

