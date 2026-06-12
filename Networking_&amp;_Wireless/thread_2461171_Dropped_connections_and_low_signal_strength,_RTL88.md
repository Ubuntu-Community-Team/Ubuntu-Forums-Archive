---
title: "Dropped connections and low signal strength, RTL8822BE card, Ubuntu 20.04"
date: 2021-04-25
forum: Networking &amp; Wireless
---

### Post by allispaul on 2021-04-25
I have a Lenovo Yoga 730 laptop running Ubuntu 20.04, with a Realtek RTL882BE wifi card. The internet is functional at home, although the signal strength is somewhat low. At my office, the wireless connection frequently drops, and sometimes the computer will stop detecting wireless networks at all. I get the sense there are some issues between Ubuntu and these Realtek chips, and I'm wondering if that's happening in my case.

I've tried reinstalling the drivers from [https://github.com/lwfinger/rtw88](https://github.com/lwfinger/rtw88), and changing the antenna selection as described there. As far as I can tell, it didn't have any effect.

Here's the output of the wireless-info script: [https://pastebin.com/1cXQPKuA](https://pastebin.com/1cXQPKuA)
I ran it from home, but can run it again from work, where the problem is worse, tomorrow.

---

### Post by CelticWarrior on 2021-04-25
Welcome.

This one seems to be the current recommendation and installing it with dkms avoids the need to reinstall whenever the kernel is upgraded: [https://askubuntu.com/questions/1263141/rtl8822be-driver-for-ubuntu-18-04-and-20-04](https://askubuntu.com/questions/1263141/rtl8822be-driver-for-ubuntu-18-04-and-20-04)

---

### Post by allispaul on 2021-04-25
Thanks! Should I be worried that the name of the driver (RTL8812AU) is different from the name of the chip?

---

### Post by CelticWarrior on 2021-04-25
No, not really.

The linked Q&A was answered by an expert. So, the driver supports several chips of the same family, the name is not that important.

---

### Post by chili555 on 2021-04-25
CelticWarrior-

The module aliases for the driver you linked don't include his device:

> Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [[COLOR="#FF0000"]10ec:b822[/COLOR]]
	Subsystem: Lenovo ThinkPad E595 [17aa:b023]

```
chili@T440p:~/rtl8812au$ modinfo 88XXau.ko | grep B822
chili@T440p:~/rtl8812au$ 
```Sorry.

---

### Post by CelticWarrior on 2021-04-25
That answer need to be corrected or deleted then. Because it was posted by Pilot6, who usually knows about this things and was accepted so...

---

### Post by chili555 on 2021-04-25
I doubt that @Yadu had the exact same b822 device. 

In any case, it is inadvisable for @allispaul to install it as we know it won't work.

---

