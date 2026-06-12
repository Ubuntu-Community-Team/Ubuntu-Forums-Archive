---
title: "No wifi after fresh install, Ubuntu 16.04"
date: 2019-09-02
forum: Networking &amp; Wireless
---

### Post by maubeh on 2019-09-02
Hello, 

I just installed Ubuntu 16.04, and I cannot detect any wifi connections. Also when I go to Settings-> Network, and to the wifi tap, when I switch it no, it immediately turns back off. 
I followed the thread on the sub-section "[Before posting in the Networking & Wireless]("https://ubuntuforums.org/showthread.php?t=2214110")". And in that thread I met the requirement to follow this  "[Broadcom guid]("https://ubuntuforums.org/showthread.php?t=2214110")" thread.
And in that thread I installed the package: bcmwl-kernel-source. And all that didn't work for me.  
I have attached the wireless-info.txt file in this thread.

Sorry for posted a related question posted earlier. I have checked most of them, but didn't work for me. Most people got help because of their machien specifications helped. 

Any help will be greatly appriciated.

---

### Post by praseodym on 2019-09-02
Your wireless is hard blocked. Any button, switch, key or key combo?

---

### Post by maubeh on 2019-09-02
Thanks for your reply. 
I have a del computer (DELL PRECISION M4800). 
You are right, the wifi signal is off, but I don't find any button or key combo to put it on!

---

### Post by chili555 on 2019-09-02
> **maubeh said:**
> Thanks for your reply. 
I have a del computer (DELL PRECISION M4800). 
You are right, the wifi signal is off, but I don't find any button or key combo to put it on!Please see: [https://www.dell.com/community/Laptops-General-Read-Only/Wifi-switch-not-working-Dell-Precision-M4800/m-p/4502828#M823583](https://www.dell.com/community/Laptops-General-Read-Only/Wifi-switch-not-working-Dell-Precision-M4800/m-p/4502828#M823583)

---

### Post by maubeh on 2019-09-02
> **praseodym said:**
> Your wireless is hard blocked. Any button, switch, key or key combo?

Hello, 
I was able to solve it given the tip you gave me!
It turns out that I don't have a key combination for it, but I had to go to BOIS settings and change wifi setting. It is explained in the solution [here]("https://ubuntuforums.org/showthread.php?t=2402062"):
Wifi should not be enabled by hardware switch.

---

