---
title: "Ubuntu 16.04 Complete Freeze when connecting to wifi"
date: 2017-03-02
forum: Networking &amp; Wireless
---

### Post by Paper Pusher on 2017-03-02
All worked well a few days ago.  Now, any attempt to connect to a wifi network causes the computer to freeze--no mouse, no keyboard.  The only thing to do is force a shutdown using the power switch.  When restarting everything seems to work properly unless I try to connect to wifi.

---

### Post by idomybest on 2017-03-05
I have exactly the same issue with exactly the same Lubuntu 16.04 update. My Rosewill RNX-N300UB USB adapter has worked fine for a year with 16.04 and all of those previous updates. It can still see all of the wifi networks in range but now completely freezes my system upon connection attempts to my network. It still functions normally tested on a Windows 7 netbook so I know its not the adapter. And all of my other wifi devices continue to connect normally so I know its not my router.

 I tried an old Linksys G USB adapter (2007 vintage) and it works just fine with this 16.04 update so I can get by for now. I have since updated to Lubuntu 16.10 but the Rosewill still behaves the same. I'm using my old Linksys until I can sort this out.

Update--- I figured out that my Rosewill RNX-N300UB USB adapter has a RealTek chipset which may need it's driver re-installed after a kernel update. I found this website [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8188CUS-and-RTL8192CU-chipsets-0bda:8176-and-0bda:8178-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8188CUS-and-RTL8192CU-chipsets-0bda:8176-and-0bda:8178-) to first identify that I had a RTL8192CU chipset (8178)and needed to jump to the content bookmark of [**2 **Realtek RTL8188CUS and RTL8192CU chipsets (0bda:8176 and 0bda:8178)]("https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8188CUS-and-RTL8192CU-chipsets-0bda:8176-and-0bda:8178-") I then followed those directions and my RNX-N300UB USB adapter is running just fine. I bookmarked this page as I may need to do this after future kernel updates.

---

### Post by lhmp1967 on 2017-03-19
Same problem after last ubuntu 16.04 update. I've found an workaround. At boot time select "4.4.0-62 generic" option.

This [ask ubuntu question]("http://askubuntu.com/questions/885427/wifi-adapter-freezes-ubuntu-16-04") could be a clue to our problem.

---

### Post by jeremy31 on 2017-03-19
The 4.4.0-66 is available now just install all updates using a working kernel and reboot.  I would check ```
dpkg -l | grep linux-image-extra
```
See if the newest linux-image-extra is an older version than the problem kernel

---

