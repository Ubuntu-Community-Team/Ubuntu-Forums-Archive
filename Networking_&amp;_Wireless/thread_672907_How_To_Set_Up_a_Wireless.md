---
title: "How To Set Up a Wireless"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by bwtranch on 2008-01-20
The first thing you need to do is find out who made the chipset. The manufacturer doesn't make any difference in so far as model. Let me explain this, a manufacturer, which I will refer to as a OEM from now on (it saves me some typing) uses whatever chips are avaiable on the open market, and this can change depending on market conditions. Just because you have say a Belkin 7050-4 today, doesn't mean that the same driver will work for somebody else tomorrow. Why? Because they might have changed the OEM chipset!

What you need to do, before you begin to waste everybody's time and your's on this forum is to determine what chipset you have. That is the only way to determine the driver that you need to get your piece of hardware working  I cannot impress this fact to you enough. Please find out who made the chip! You can Google for it or contact the OEM or visit their website. Then, and only then, can someone help you to find the right driver and install it. 

Valuable time and resources are being used on this forum by people not understanding this concept. After you know what chipset you have and posting the output of lspci and/or lsusb, then we can save everyone a lot of time. Thank You.

---

### Post by rosegarden78 on 2008-01-20
I had that problem with a Dell BCM43xx back in the days of Edgy Eft.  Now it's so easy with Gutsy Gibbon.  But you do need to get the name of the firmware if your card is unsupported.  Google?  Firmware Rippers?  What did I use back them?

Anyway I installed and modprobed the bcm43xx and that's how I got mine working.

---

