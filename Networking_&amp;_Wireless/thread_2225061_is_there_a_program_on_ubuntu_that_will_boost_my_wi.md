---
title: "is there a program on ubuntu that will boost my wifi"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by joshua20 on 2014-05-19
so i have wifi in my home i live on the third floor and i get one bar in most places and to connect i have to be in the right spot so is there a way to boost my laptops wifi resever with a program i know i can just buy a better wifi router but just want to know if there's any program before i do that

---

### Post by kurt18947 on 2014-05-19
I've never heard of one.  Are you using an internal WiFi card?  If so I doubt that a different USB adapter would help.  If the signal is better in one spot than in others, you could possibly consider a repeater.  Here is what Newegg offers:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=wifi+repeater&N=-1&isNodeId=1](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=wifi+repeater&N=-1&isNodeId=1)

Do they work or how well do they work?  I have no experience.  Some USB wifi adapters can fit external antennas.  I don't know if they'd be better than internal wifi cards or not.  I do know that not all USB adapters are equal re signal strength.  My Trendnet TEW-649UB (Realtek 8192SU chip) indicates very good signal strength.  I have a couple Ralink/Mediatek RT5370 adapters that do not have as good signal strength.

Edit:  on second thought, if you're using drivers that come with Ubuntu and the manufacturer offers a proprietary driver,  sometimes using the proprietary driver offers better performance than the open source driver.  I've heard this is true of the Ralink RT5370 I mentioned above and it's true of the RealTek 8192CU chipset as well.  Proprietary drivers would need to be built and rebuilt each time the kernel is updated unless it supports DKMS.

---

