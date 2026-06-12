---
title: "Wireless Card Recommendations?"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by frank_costanza on 2007-04-18
I was finally able to get my Compaq V3000's wireless card recognized by Ubuntu using ndiswrapper. However, it won't connect to my network using WPA.

I'm looking to get a new wireless card (mini PCI) because I'm tired of trying to get my current card to work. I currently have a crappy Broadcom 4311. I've heard that the Intel 9465 is supported natively. Does anyone know if it plays nicely inside an AMD Turion 64x2 laptop?

Any other mini PCI wireless card recommendations?

---

### Post by frank_costanza on 2007-04-21
I installed the latest Ubuntu updates, and somehow, I am now able to use WiFi via ndiswrapper, my Broadcom 4311, and WPA2 encryption. However, it doesn't always connect immediately. It took about five minutes. But now that I'm connected, I have excellent download speeds.

One thing that is strange is that the connection strength is only rated at about 65% but my access point is about 12 feet away.

Anyway, I wish I could give advice to others on how I got it to work. I mostly just followed one of the Broadcom tutorials. I know I had to blacklist the default 43xx driver and I also had to comment out everything in /etc/network/interfaces except:

auto lo
iface lo inet loopback

Incidentally, the default 43xx drivers eventually worked for me, but the download speeds were like dial-up, so that's why I used ndiswrapper.

Anyway, wireless was one of the things that was holding me back from using Ubuntu full-time. Now, I just need to get the APCI stuff working. Beryl would also be nice, but not a deal-breaker for now.

---

