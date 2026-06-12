---
title: "Wireless PCMCIA Freeze System After A While"
date: 2005-03-28
forum: Networking &amp; Wireless
---

### Post by ranger79 on 2005-03-28
Hi,

I have Hoary installed on my Acer TravelMate 650 successfully.

I haven't tried things like the Firewire, Card Reader etc. Currently I'm having problem configuring my Creative Network Blaster Wireless card. Although this card is not formally supported in the atmelwlandriver, I found this page [Yakumo](http://www.lug-bs.de/lug/leute/c.borss/wlan/minihowto-yakumo-pcmcia-wlan-card.txt)  that describe the driver for Yakumo, which is the same as my card. (Confirmed via the FCCID search page.)

I've uninstalled the atmelwlandriver.2.1.1 installed via the Synaptic and compiled the atmelwlandriver-3.4.1.0 downloaded from the atmelwlandriver web page.

With the latest driver, I've been able to get the card recognized and working properly for a while. The driver, however, caused the system to completely freeze after 10 to 20 minutes.

I'm sorry I'm not able to post any messages, as it's a complete freeze.

Appreciate very much if any one can give any hints to solve this problem.

Thanks.

---

### Post by ranger79 on 2005-03-31
Any update from any one?

I noticed that the atmelwlandriver come with Hoary is version 2.1.1 but the latest version is 3.4. Does any one know why is such big different in the versions?

Thanks.

---

### Post by simscitizen on 2005-04-01
I have the same problem with my Atmel card (a 3Com 3CRSHPW196). Every ~20 minutes or so, it stops working and i have to deactivate/reactivate in the networking panel before it starts working again. A huge pain, and it makes Ubuntu rather useless. I had the same problem in Warty, but I gave up pretty fast; now I'm hoping someone will be able to fix/help with the problem.

I'm not using atmelwlandriver, but rather the atmel firemware loader from the [email]simon@thekelleys.org.uk[/email] guy. The atmel driver (from what I understand) is already built in to 2.6.x kernels, but it's a bit buggy so you need simon's loader (available off universe i think) to make the kernel driver work.

---

### Post by fergal on 2006-04-30
simscitizen, I have the same problem. I found that running a ping in the background keep the connection alive. I've installed the atmel-firmware package but no luck. I've also tried loading firmware by hand.

I think I'll just sart up a constant ping.

---

