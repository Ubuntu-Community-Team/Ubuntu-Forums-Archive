---
title: "USB Wireless Adapter Needed"
date: 2015-07-26
forum: Networking &amp; Wireless
---

### Post by aaroncampbell2 on 2015-07-26
I recently got a new Samsung ATIV Book 9 Plus NP940X3K-K02US. Unfortunately, the [wireless on it isn't working with Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184"), which is kind of a big deal for me. I'd like to get a USB wireless adapter to use in the interim, but obviously I want to make sure I get something that will just work out of the box. My wireless network here supports AC/N/G/B (it uses all ASUS RT-AC66U routers).

Does anyone have a recommendation? Preferably one they've used and know works?

I'm on Ubuntu 15.04

---

### Post by howefield on 2015-07-26
Thread moved to the "*Networking & Wireless*" forum. You'll get netter support in here.

---

### Post by aaroncampbell2 on 2015-07-26
I just realized there was a "Networking & Wireless" forum, and I posted this in "hardware". I came back to see if there was a way for me to move it, and it was already moved! Thanks to whoever did that.

Edit: Thanks howefield :)

---

### Post by Vladlenin5000 on 2015-07-26
Post #177 in [your link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184") points to a solution.

---

### Post by aaroncampbell2 on 2015-07-26
Thanks for pointing that out, but I've tried every solution in that thread (and there are several, including #115, #150, #177, #189/190, and #201). It's entirely likely that I'm messing something up, but none of them have worked for me. That's why I'm looking to get a USB adapter to use until one does.

---

### Post by Vladlenin5000 on 2015-07-26
Post #177 has links for driver and firmware. Have you tried to use those? If so, how?
You may have missed some step... Or forgot to blacklist some other driver... Or...

---

### Post by aaroncampbell2 on 2015-07-26
> **Vladlenin5000 said:**
> Post #177 has links for driver and firmware. Have you tried to use those? If so, how?
You may have missed some step... Or forgot to blacklist some other driver... Or...

I got the firmware first, copied the ath10k directory to /lib/firmware as it instructed. The other seems to be building a kernel, something I haven't done in probably 15+ years. I ran `make config`, answered about 1m questions all with defaults since I didn't know on 99.9% of them, then ran `make`. I haven't been able to successfully boot to the new kernel though, thus me being pretty sure it's my own shortcoming. Still, since I can't get that to work and I know it will be fixed at some point anyway, I'd like to get a USB adapter to use for now...which is what caused me to open this thread.

---

### Post by praseodym on 2015-07-26
Try this:

[https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658](https://forum.ubuntuusers.de/topic/kein-treiber-fuer-qualcomm-atheros-qca61x4-wir/#post-7677658)

The link in #4 is installing the backport drivers, please see there

---

### Post by aaroncampbell2 on 2015-07-26
I tried doing that already (there were similar English instructions somewhere). The problem I have is when I get to custom compiling backports ([https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports)) from the source. It needs spatch > 1.0.0-rc24 but I only have spatch 1.0.0rc22. I tried to use the ppa ([https://launchpad.net/~npalix/+archive/ubuntu/coccinelle](https://launchpad.net/~npalix/+archive/ubuntu/coccinelle)) but it only has rc22 as well. I tried to do that from source as well, but ran into another issue (that I can't remember now). At that point I felt like I was further down the rabbit hole than really made sense. I doubled back, and tried the section titled "ath10k backports releases" on [https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports). I tested the latest stable non RC, the latest stable RC, and the latest dev, using each with the instructions you linked and restarting after each. None of them made the wireless show in my wireless manager or ifconfig.

---

### Post by aaroncampbell2 on 2015-07-27
This thread got pretty hung up on fixing the original issue rather than  recommending actual options, so I just went ahead and bought this [Edimax EW-7811Un]("http://smile.amazon.com/dp/B003MTTJOY")

I'll  post back here in a few days after I test it out in case anyone else  has similar needs, and hopefully when my built in wireless adapter is  supported, I'll move this over to one of my Raspberry Pis :).

---

### Post by weatherman2 on 2015-07-28
It looks like that Edimax dongle has the Realtek 8192CU chipset - I have a couple of dongles with that chipset.  For some reason, for years, the Ubuntu driver has been broken for this chipset, and even as of Ubuntu 14.04.2 you still have to build an updated driver to get it to work reliably.  15.04?  Not sure, but I'd guess you're still going to have to build it.

Here's what I used to build it:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

Probably a lot simpler than fixing your internal wireless card...but, this is not exactly a speedy wireless card even when working perfectly.  It's only 150Mbps, so if you have an AC router that's pretty slow.   But in a pinch, it should work.

If it happens to be easy to access your internal wireless card physically, another solution may be simply to replace the internal wireless card with a card that has better Ubuntu support.  I've upgraded lots of laptop wireless cards, but sometimes they are not easy to access.  Sometimes they are.

---

### Post by howefield on 2015-07-28
Have a browse here,

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://www.ubuntu.com/certification/catalog/category/WIRELESS/](http://www.ubuntu.com/certification/catalog/category/WIRELESS/)
[http://www.linuxwireless.org/en/users/Devices/](http://www.linuxwireless.org/en/users/Devices/)

---

### Post by aaroncampbell2 on 2015-07-29
> **howefield said:**
> Have a browse here,

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://www.ubuntu.com/certification/catalog/category/WIRELESS/](http://www.ubuntu.com/certification/catalog/category/WIRELESS/)
[http://www.linuxwireless.org/en/users/Devices/](http://www.linuxwireless.org/en/users/Devices/)

Thank you again Howefield. I only wish it would have come in before I had bought.

Luckily:

> **weatherman2 said:**
> Here's what I used to build it:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)


Thanks a TON, that worked perfectly!

---

