---
title: "ndiswrapper and Broadcom BCM4303"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Cristatus on 2007-06-26
Hi. I am very new to the linux scene, and especially Ubuntu.

I am currently trying to get my desktop to run Ubuntu. It runs ok so far, except that I need internet on the machine. I have a Linksys WMP 11 with a Broadcom BCM4303 chipset.

I have installed ndiswrapper to let me able to use my wireless card, but that made my "Network settings" lose my card. I assume that's OK, because when I tried out SuSE (about 2 years ago) i had to use some commands in the terminal to make the card scan for wireless networks, which I do no remember right now.

My questions are as follows:
1. Is it normal that there is no more wireless adapter in "Network settings"
2. How do I scan for available networks?
3. I have a WEP key that I know the HEX values of. Will I be able to use this key? Or will have to turn of WEP?
4. My network is set up with static IPs. Does that change any of my settings in ndiswrapper?

Thanks in advance.

PS: if you require any information, please don't hesitate to ask.

(C)

---

### Post by Cristatus on 2007-06-28
Ok, I've got the wireless adapter to show up in the "Network settings", but when I scan for wireless networks with "iwlist [*interface*] scanning" I get no results. I know there is a connection available (in fact, there should be at least two APs visible) because I'm scanning from my laptop sitting right next to my desktop.

I still don't know how to figure out static IPs in the network though, but that shouldn't make a difference as to whether I can see any available APs.

(C)

---

