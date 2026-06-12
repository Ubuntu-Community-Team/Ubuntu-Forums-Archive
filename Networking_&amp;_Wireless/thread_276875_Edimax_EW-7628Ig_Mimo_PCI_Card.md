---
title: "Edimax EW-7628Ig Mimo PCI Card"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by k@y@ on 2006-10-13
Hi to all.

Using ubuntu for a few months and very pleased with this os. But since i've bought a new wireless card today, had a problem :(

I've just done a search but found no information about [this wireless card]("http://www.edimax.com.tw/html/english/products/EW-7628Ig.htm") on ubuntu forums. I couldn't connect internet with this card. What do you suggest? Any solution? Or should i go to my reseller to change this card with us-r maxg or another one?

---

### Post by ciax on 2006-12-02
Hi,
just install rt61 driver for linux, in fact such a wifi-card is based on rt61 wireless chipset:

[http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz]("http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz")

Extract it:

*tar xvf RT61_Linux_STA_Drv1.1.0.0.tar.gz*

and follow the instructions in the readme file *RT61_Linux_STA_Drv1.1.0.0/Module/readme*

Moreover, I strongly suggest to look [in this previous post]("http://ubuntuforums.org/showpost.php?p=1678002&postcount=26") for a detailed explaination.

Works for me...

bye



> **k@y@ said:**
> Hi to all.

Using ubuntu for a few months and very pleased with this os. But since i've bought a new wireless card today, had a problem :(

I've just done a search but found no information about [this wireless card]("http://www.edimax.com.tw/html/english/products/EW-7628Ig.htm") on ubuntu forums. I couldn't connect internet with this card. What do you suggest? Any solution? Or should i go to my reseller to change this card with us-r maxg or another one?

---

