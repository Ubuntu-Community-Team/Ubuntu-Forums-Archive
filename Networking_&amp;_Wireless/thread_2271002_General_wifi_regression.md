---
title: "General wifi regression?"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by kjano on 2015-03-26
Hi all,

I am have numerous laptops in my group, all running Ubuntu 14.04 or 14.10 and all of them have some sort of wifi issue.  It seems like there is a general regression with respect to wifi support on Ubuntu and probably Linux in general. This is very surprising as wifi is one of the most important components for everyday work and laptops from Lenovo are usually very well supported. I cannot get a stable and work-quality wifi connection on any of these laptops:  ASUS N550JV, Lenovo T440S,P, T540, X1 2013, and MacBook Pro 15 2013. I realize that the Ubuntu forum is full of complains and potential solutions for those wifi issues and that there are many reports on bugs.launchpad.net. Essentially, wifi is not usable on T440S,P and T540, drops connection frequently on Asus N550JV. Wifi quality on the MacBook Pro 15 2013 and X1 is fair but only if the wifi signal is strong. I have not started this thread to find a solution but to figure out whether this is part of a bigger picture and what may be causing this wifi regression. I would have assumed that more and more manufacturers are providing drivers for their hardware or has this trend stopped for some reason? Also, in the past, Lenovo (and IBM) were actively advertising their Linux support and drivers were rarely a problem?

What is your opinion?

Best,
Chris.

---

### Post by weatherman2 on 2015-03-26
In my opinion, wireless card support in Linux varies more* by manufacturer of the wireless card *than by manufacturer of the laptop.  In other words, look at not how well Asus or Lenovo supposedly support WiFi but at how well Intel, Broadcom, Atheros, etc. (the card manufacturers) support it.  I always look at how well any wireless card I might want to use in Linux is supported before committing to it.

The wireless card drivers should be built right into the kernel, unless the card is still too new to have the drivers included in the kernel you are using...or because the best available driver isn't completely "open source" (so may need to be post-installed as an "additional driver.").

I support or own six different laptops running Ubuntu 12.04.  All of them have excellent wireless performance.  (I've also booted 14.04 on some of these laptops and not noticed any wireless issues in my brief evaluations.)  All of them also have Intel wireless cards.  In my experience, Intel wireless cards are the most likely to work out-of-the-box without tweaks than the others.  Though I've seen reports here about people having Ubuntu issues with Intel cards, I've seen none myself and not needed to do any tweaking.  Other cards from other manufacturers may also work well automatically but often seem to need more tweaking.  I've booted Ubuntu on lots of laptops with Broadcom and Atheros cards.  Some of them seem to work perfectly, others require additional drivers or tweaking.  Some of them I replaced with Intel cards, knowing I wouldn't have to do any tweaking in the future.

I've successfully upgraded the wireless card in almost every laptop I've ever owned (largely Dells).  I don't buy Lenovo (or HP) laptops because those companies "whitelist" their wireless cards, so that you can only install an internal wireless card approved by the laptop manufacturer for that specific laptop (so maybe only 2 or 3 models, at most).  Otherwise, it won't even POST until you remove the non-approved card.  I don't like not having the ability to change my hardware to something known to work better in Linux.  Swapping out a laptop wireless card is often easy (occasionally a pain if the card is buried inside the laptop under the keyboard) and often cheap.  The Intel 6235 dual band 802.11n card with bluetooth could be had as cheap as $12 USD on sale on eBay, and I've installed a couple of them now.

If you really want to improve the wireless performance if your laptops, you need to look at each one on a case-by-case basis.  See what wireless cards they have and if any are known to have issues or could be improved with tweaking.  You may even consider upgrading some of the wireless cards (not the Lenovos of course).  You may also want to look at the wireless infrastructure you use - what access points, etc.  Are you really seeing Windows or Apple laptops working with solid WiFi performance next to Ubuntu laptops that have lousy connections?  Otherwise, what's your basis for comparison?  Do you work in an area with a lot of 2.4GHZ WiFi access points that can interfere with each other?  Have you tried 5GHZ too?

---

### Post by pfeiffep on 2015-03-27
> **kjano said:**
> Hi all,

I am have numerous laptops in my group, all running Ubuntu 14.04 or 14.10 and all of them have some sort of wifi issue.  It seems like there is a general regression with respect to wifi support on Ubuntu and probably Linux in general. This is very surprising as wifi is one of the most important components for everyday work and laptops from Lenovo are usually very well supported. I cannot get a stable and work-quality wifi connection on any of these laptops:  ASUS N550JV, Lenovo T440S,P, T540, X1 2013, and MacBook Pro 15 2013. I realize that the Ubuntu forum is full of complains and potential solutions for those wifi issues and that there are many reports on bugs.launchpad.net. Essentially, wifi is not usable on T440S,P and T540, drops connection frequently on Asus N550JV. **Wifi quality on the MacBook Pro 15 2013 and X1 is fair but only if the wifi signal is strong**. I have not started this thread to find a solution but to figure out whether this is part of a bigger picture and what may be causing this wifi regression. I would have assumed that more and more manufacturers are providing drivers for their hardware or has this trend stopped for some reason? Also, in the past, Lenovo (and IBM) were actively advertising their Linux support and drivers were rarely a problem?

What is your opinion?

Best,
Chris.I have found just the opposite, one of the latest software releases for Ubuntu 14.04 LTS has IMPROVED the wifi stability on my Dell Laptop [Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)]. I've bolded a sentence that, IMO, suggests a router or distance from router issue. The Mac Book Pro in our household is stable when wifi connected.

---

### Post by slickymaster on 2015-03-27
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by kjano on 2015-04-26
ASUS N550JV just went from weak and unstable wifi to no wifi at all after updating to 15.04. Maybe some card are getting better support but in far too many cases there is a wifi regression. Lack of wifi on all Lenovo T440/540/450/550 alone is a huge issue.

---

### Post by jeremy31 on 2015-04-26
> **kjano said:**
> ASUS N550JV just went from weak and unstable wifi to no wifi at all after updating to 15.04. Maybe some card are getting better support but in far too many cases there is a wifi regression. Lack of wifi on all Lenovo T440/540/450/550 alone is a huge issue.

What wifi cards do you have?  And are they hard blocked?```
lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by kurt18947 on 2015-04-26
> **kjano said:**
> ASUS N550JV just went from weak and unstable wifi to no wifi at all after updating to 15.04. Maybe some card are getting better support but in far too many cases there is a wifi regression. Lack of wifi on all Lenovo T440/540/450/550 alone is a huge issue.

Is this off one WiFi access point, or several of the same make/model? If it were me, I'd buy an adapter or two known to work well - something like a TrendNet TEW-649UB (uses a Realtek 8192SU chipset AFAIK) or Netgear WNA1100 (Uses an Atheros 9271 chipset though limited to 150 mb/sec. Try one of those on your problem machines and see if they work better. If not I'd wonder about the access point(s). My newest Thinkpad is an X201 with an Intel 6200 wifi chipset running Xubuntu 15.04. It works quite well and is stable. My wifi router is a Linksys E2500 running DD-WRT.

---

