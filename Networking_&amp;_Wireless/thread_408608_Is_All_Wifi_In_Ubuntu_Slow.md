---
title: "Is All Wifi In Ubuntu Slow?"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by TheVault on 2007-04-13
This problem is really killing me. I would like to know if all Wifi in Ubuntu is slow? I'm sitting upstairs on a Broadcom 4311 Chipset driver on my Dell Inspiron E1405 computer. Anyway, since upgrading to feisty, well I gotta admit the wifi is easier to connect to. But the problem still remains, slow browsing/downloading. On Windows, I download quickly and browse quickly with ease. On Ubuntu, pages load up but not like on Windows, kinda take its good old time. Its kinda like Dial Up on Ubuntu with the wireless.

I don't mean to talk bad about Ubuntu(at least I don't think I am) but Wifi for ubuntu is super slow. I was even sitting downstairs, closer to the router, and it was still browsing & downlaoding slow. Its tolerable, don't get me wrong, but I would like to know if all wifi in ubuntu is the same?

Some info about this would be greatly appreciated. Thanks.

---

### Post by happy-and-lost on 2007-04-13
Sounds like you may be using the wrong driver. Try *dmesg | grep bcm* to see if there are any driver errors.

---

### Post by alex_anthony on 2007-04-13
I found that I got better speed at distance from my router with ubuntu over windows, so definitely check your driver

---

### Post by TheVault on 2007-04-13
Hmmm Iv heard about the driver thing as well, check your driver. well I was in the #ubuntu+1 chatroom and I was told me to use this under my respitories.

[http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) dapper-cafeugo bcm43xx

but in the proper format. Anyway, then they said sudo modprobe bcm43xx and then I restarted my computer and BAM, wireless was working again. No ndiswrapper or bcm43xx-fwcutter or anything, that got me online real quick. So, maybe you guys know of another way? Or maybe a more updated driver for Broadcom 4311?

---

### Post by srt4play on 2007-04-13
The bcm43xx driver supports only 802.11b 11Mb/s speed.  Believe me it's worth the time to setup ndiswrapper to get 54Mb/s.

---

### Post by TheVault on 2007-04-13
> **srt4play said:**
> The bcm43xx driver supports only 802.11b 11Mb/s speed.  Believe me it's worth the time to setup ndiswrapper to get 54Mb/s.

Holy cow, talk about fast browsing. Now its just as fast as my windows browsing. I had no idea, but thanks to you, I'm not browsing just as fast. Thank you so much much for helping me. I found some useful tutorials & now I'm a happy wireless camper. Thanks again!

---

### Post by srt4play on 2007-04-13
Hey TheVault, good job!

I was just about to post some instructions for you, glad you got it figured out!

---

### Post by Druke on 2007-05-18
> **srt4play said:**
> The bcm43xx driver supports only 802.11b 11Mb/s speed.  Believe me it's worth the time to setup ndiswrapper to get 54Mb/s.

what windows driver do i get if the 43xx-fwcutter worked for me, I'm tired of this slow wifi

---

### Post by Old *ix Geek on 2007-05-20
> **srt4play said:**
> The bcm43xx driver supports only 802.11b 11Mb/s speed.  Believe me it's worth the time to setup ndiswrapper to get 54Mb/s.

I wish it would work for me!  I've followed everything to the letter and still have the slowest, most painful Internet (and network) connections I've seen since the bad old days of 2400 baud dialup modems.  I wonder what I'm missing?!

---

### Post by H.E. Pennypacker on 2007-05-27
> Holy cow, talk about fast browsing. Now its just as fast as my windows browsing. I had no idea, but thanks to you, I'm not browsing just as fast. Thank you so much much for helping me. I found some useful tutorials & now I'm a happy wireless camper. Thanks again!

Unfortunately, the open source driver is not as fast as the proprietary driver.  You were using the open source driver.

> what windows driver do i get if the 43xx-fwcutter worked for me, I'm tired of this slow wifi

Use the proprietary driver (bcm5wl.inf).  Use the various guides available on these forums to see how to connect exactly.

> I wish it would work for me! I've followed everything to the letter and still have the slowest, most painful Internet (and network) connections I've seen since the bad old days of 2400 baud dialup modems. I wonder what I'm missing?!


You followed which guide to the letter?  Please refer to that guide's thread, and there may be more out there who are experiencing the same problem.  You'll be better off following and staying with the thread that originally helped you connect to the Internet.

---

