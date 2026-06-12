---
title: "Ubuntu 14.04 lts No network devices available"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by acie312 on 2015-08-21
I am a very newbie to linux. I recently tried to dual boot my laptop with windows 10 and ubuntu, but accidentally (or "stupidly" rather) installed ubuntu os on top of windows os; as the result, my windows is gone now and I can't set up wifi on ubuntu 14.04. It said no network devices available. I had tried many way like update or install driver, but nothing works. Some errors I kept getting were: unable to locate package, failed to fetch (when run apt-get update), lo no wireless extensions (when run iwconfig)
My laptop model is Acer Aspire r7
The network controller is Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

I really really need help. I can't use my laptop at all now. Thank you

---

### Post by TheFu on 2015-08-22
a) you can use the "converter port" to use an RJ45 connector for a wired ethernet connection.  Wired is **always** better than wifi. Always.

b) [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) appears to have a solution using a proprietary driver. If this becomes a hassle to rebuild the driver for every kernel, then you might just buy a tiny USB wifi dongle that is supported by Linux natively.

You will probably need "a" get make "b" work.

---

