---
title: "Wireless Freezing my comp in 7.10"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by F4ll3ngo3th3 on 2007-12-02
I'm a new Ubuntu User and I had just finished installing it a few hours ago. I'm still suffering from culture shock but the internet had been a really great help. I'm now able to dual-boot Ubuntu and Vista with no problem...

However, I have a problem with connecting to the internet through Ubuntu 7.10

It recognizes my adapter and even scans the wireless networks around me, but, when I try to connect on my home network, it hard freezes.

I've been looking all over the internet for a solution but I just can't find any. When I boot to Vista (which I'm on rite now), the internet works fine. My Wireless card is a Realtek 8185 Extensible 802.11b/g Wireless Device. I've seen from [https://help.ubuntu.com/community/Ha...rkCardsRealTek](https://help.ubuntu.com/community/Ha...rkCardsRealTek) that 8185 is supported in 6.06 and 6.10 with no problems.

Since I have a fresh install, I could always switch to 6.10. I installed 7.10 thinking that it would be the most compatible but I guess I was wrong. Maybe 7.4 would be okay too. The problem is that, it's kinda frustrating if I have to re-install Ubuntu versions just to make my internet work. If there is a way to downgrade, I guess it would be a lot more easier.

---

### Post by abdrahmanh on 2007-12-03
Hi, 
i got kinda same problem .... wireless usb adapter DLInk DWL G122 F/W Ver 3.00  H/W Ver C1
Connection fine with XP but wireless missing in Ubuntu....:confused:
I would like to just remove the rta drivers I installed.. got messed up I guess.... pls help me out with this..... anyone

---

### Post by climatewarrior on 2007-12-03
Most likely Ubuntu assinged an opensource driver that isntt very friendly with your wireless card. My recommendation is to disable that driver and use the windows driver instead with ndiswrapper. But dont do anything just yet. Wait for more responses. Also I will take this time to tell you that if there is something that can be a pain in the *** in linux is wireless internet. And this is not Linux's fault. It is the fault of the hardware manufacturers that dont release wireless drivers for linux. But after you properly set them up they wont bother you at all. Linux can sometimes be hard to setup (although sometines it can be easier to setup than Windows) but after that initial state you will have a nice and stable OS.

Aniway Just my opinion.

Good Luxk

---

### Post by abdrahmanh on 2007-12-03
Now, if I use Windows driver via ndiswrapper ..... will it overwrite the already installed Ralink rta drivers....:confused:

---

### Post by climatewarrior on 2007-12-03
>  Iif I use Windows driver via ndiswrapper ..... will it overwrite the already installed Ralink rta drivers..
Not necessarilly, how did you install those drivers?

---

