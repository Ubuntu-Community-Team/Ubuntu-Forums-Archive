---
title: "Issue with iBook G4 Airport Extreme card (Device not ready(firmware missing))"
date: 2015-03-04
forum: Networking &amp; Wireless
---

### Post by cameron20 on 2015-03-04
Hello,
I'm having a problem with an iBook G4 PowerPC. I recently got it out of storage because I wanted to give it to my mom and put Ubuntu on it. On eBay, I bought it an Airport Extreme card. When installing the card, I then booted up the system. I got the message "Device not ready (firmware missing)" and it didn't find any wireless networks. I'm assuming I need a driver. The iBook doesn't have any wireless connectivity at all, but I can install packages with my computer and transfer them to my iBook through USB. The iBook is running Ubuntu 12.04. If you give me a package to install, please explain how to install it. I'm new when it comes to the terminal. Any help would be appreciated! :)

---

### Post by chili555 on 2015-03-04
I doubt that you need a driver; I suspect you need firmware! Let's start by identifying your wireless card. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my keyboard on the same key with \. 

If it is a Broadcom, please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by cameron20 on 2015-03-05
Sorry for the late response, but according to what it says, I think it's broadcom:
0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
I'll check the link now.

[B]Edit: I can't get any internet on this computer as far as I know. I tried a wireless USB dongle and it still didn't connect to it. In my house, there is no Ethernet that I can use. Can you get the packages for me to download? Thanks for your help!
[/B]

---

### Post by Hadaka on 2015-03-05
Hi, here you go,no internet required..
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
post #7...be sure to download the b43.zip file first.
thanks

---

### Post by cameron20 on 2015-03-05
I think I am going to install another distro of Ubuntu on it because it doesn't run very well, but thank you!

---

### Post by chili555 on 2015-03-05
Since the wireless device will be the same, the firmware installation will be the same. Good luck and let us know if you need more help.

---

