---
title: "changing my wifi card"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by robstat on 2007-04-08
I am quite new to linux and am struggling to sort out my wifi I have a HP pavillion dv6000 laptop with a broadcom bcm4310 chip. I have tried ndiswrapper and fwcutter with no joy, so i've decided to save myself the headache and change the chip with one that works out of the box.
What I need to know is what chips can i change it for that will work? and will any chip fit or do they come different sizes and pin configurations? Many thanks in advance..
P.S. I'm running 7.04 beta(amd64) but can install any if it will work.

---

### Post by Swab on 2007-04-08
I think most wifi in laptops is supplied by a mini PCI card.

More info here: [http://en.wikipedia.org/wiki/Mini_PCI](http://en.wikipedia.org/wiki/Mini_PCI)

---

### Post by chibiace on 2007-04-08
im quite happy with the intel wireless that came with my laptop. uses the ipw2200 driver, works out of the box. hurray for pentium m centrino packages.

---

### Post by robstat on 2007-04-09
Thankyou for such a speedy response. I thought they came in different sizes, so I change it like for like. I have searched google but can't find any information on which size mine is , does anyone where I can find this information?

---

### Post by Swab on 2007-04-09
I guess you need to pull it out and take a look...

---

### Post by robstat on 2007-04-09
I have taken the minipci card out to measure it and it doesn't match any listed on wiki, it measures 30mm x 50.7mm which is quite abit smaller than anything else on there! the numbers on the card were
bcm4311kfbg
ca0622 p11
785289 n1
Any ideas where to go from here?

---

### Post by robstat on 2007-04-13
Is this my wifi card? Or is it my ethernet card someone told me that my wifi card should be under the keyboard and this under a cover on the bottom of the laptop???

---

### Post by Mr Squiddy on 2007-04-13
I had the same issue as you with a difficult-to-configure Broadcom 4318 wireless card.  In the end I replaced it with an Intel PRO 2200 and it worked perfectly from the start.

---

