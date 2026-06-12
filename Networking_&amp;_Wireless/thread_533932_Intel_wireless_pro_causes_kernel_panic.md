---
title: "Intel wireless pro causes kernel panic"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by swinky on 2007-08-24
I'm using an IBM Thinkpad T40, running Ubuntu 7.04.  I've been having an issue with my Intel Pro/Wireless 2100 3B Mini PCI Adapter.  It connects to my network okay, but will every now and then drop the signal completely (despite me being about 5 feet away from my wireless router), so I decided to look around on the internet to try and fix it.

Then I broke it.

I was following some directions that I found through thinkwiki.org, though I can't find them any more.  I'm not *entirely* sure what I did, but I downloaded and reinstalled ipw2100 and ieee80211 (because ipw2100 said it required it,) and I think wireless tools (I know I tried but I don't remember if it installed correctly.)  I also got the new firmware files but wasn't entirely sure where to put them.  I saw it mentioned on a few websites to put them in the /lib/firmware/2.6.20-16-generic folder, so I put them there.

Well... now whenever I try to boot with 2.6.20-16, it stops booting as soon as the wifi light comes on.  If I run recovery mode, sometimes it will boot, other times I get an error that reads something like "can't sync - Kernel panic" and something about "failure" and "interrupt."  I don't recall exactly what it was because I'm currently using the laptop with 2.6.20-15-generic, which works fine.  The error also comes with "Code:" followed by a long string of hex bytes.  On the rare occasion that I can boot, the laptop freezes as soon as it tries to connect to a wireless network. 

So I admit I'm kind of a newbie, but I don't really know where to start fixing this.  Any help would be greatly appreciated, even if only how to disable the wireless long enough to boot into the newer kernel.  Last thing I want to do is start messing around with more stuff and make both kernels fail to boot.

---

### Post by jrusso2 on 2007-08-24
I am not sure how to fix your problem, I think you loaded stuff that you already had.  The problem with the Intel wireless connecting and reconnecting seems to be common.  I have that problem with some routers even with Windows XP.

It might be caused by some imcompatiability with the Intel wireless and the chip used in your wireless router.

But I have noticed many complaints about this issue.

---

