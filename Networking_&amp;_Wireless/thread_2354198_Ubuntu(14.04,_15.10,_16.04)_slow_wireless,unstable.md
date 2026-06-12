---
title: "Ubuntu(14.04, 15.10, 16.04) slow wireless,unstable connection Atheros QCA9565 / AR956"
date: 2017-02-28
forum: Networking &amp; Wireless
---

### Post by vioreld on 2017-02-28
So, I have installed a few versions of Ubuntu, 14.04, 15.10,  16.04.After that I've installed Linux Mint 18.1 just to come back at  Ubuntu 16.04(with every try dual-boot Windows 10). 

  
The reason why I've been through all these versions is because I've  had unstable and very slow wireless connection(about 15x slower in  comparison with Windows 10) no matter the case. I've tried what  seemed to be working for other users, even if my problem wasn't exactly  the same. I even tried upgrading to kernel 4.10 but the problem is still  there.

  
Something interesting is, while I have Ubuntu/Linux Mint installed,  when I switch to Windows 10 I have the same issue as mentioned, plus the clock is off and bluetooth driver is stopped by Windows. If I  remove Ubuntu/Linux Mint the problem goes away and everything is back to  normal.

  
Here's my wireless-script result: [http://pastebin.com/YCGr8Xc1](http://pastebin.com/YCGr8Xc1)

  
I may add the fact that Windows 10 and Ubuntu are installed on separate partitions.

  Thanks in advance!

---

### Post by jeremy31 on 2017-02-28
Can you change encryption on the wifi router to WPA2 only instead of using WPA/WPA2?  The bluetooth issue might just happen when rebooting from Ubuntu/Linux to Windows instead of shutting down the computer when switching between Linux and Windows, which would indicate that the firmware remains loaded in the bluetooth chipset during reboot

---

### Post by vioreld on 2017-03-01
First of all, thank you for your reply.It is kind of funny because I've tried different things that required a lot more time than this. I have changed the encryption to WPA2 and everything seems to be working, but I'm using a different router than the one I've used for the wireless-script. I'll be testing the other one in the weekend and I will post an update :)

---

### Post by vioreld on 2017-03-03
Update: Doesn't seem to be working. Same problem on Ubuntu and Windows 10.

---

### Post by jeremy31 on 2017-03-03
That last post might reveal that is an issue with the access point.  Hardware manufacturer's spend a lot of money to make sure their hardware works in Windows in any environment

---

### Post by vioreld on 2017-03-04
Probably, but I've noticed that the problem affects Windows only if I boot on Ubuntu and then restart to boot into Windows. If I do "shutdown 0" and then power up the laptop to firstly boot in Windows it works at usual, no problems. I've seen many posts about QCA9565 having problems in Ubuntu/Linux so it may be a compatibility issue, I assume. I'll be looking forward for some solutions because it really bugs me. Thanks :)

---

