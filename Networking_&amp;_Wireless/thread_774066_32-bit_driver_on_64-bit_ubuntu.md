---
title: "32-bit driver on 64-bit ubuntu?"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Dinchamion on 2008-04-29
So here is my problem: I have a 64-bit processor, and naturally, I would like to use 64-bit linux as well. However, I use a wireless network to connect to the internet (sharing a DSL line between three computers at home, plus my laptop in a few weeks -- hopefully there I won't have this problem), and my desktop PC has a [TP-LINK TL-WN651g](http://www.tp-link.com/products/product_des.asp?id=17) wireless card.

As far as I know, there are only 32-bit drivers for this card to use with Windows and ndiswrapper.

So far it wasn't a problem, but I'm starting to do some sensitive work (3D modelling, etc.) and I'd like to use my system on full capacity, this is why I'm trying to get it working with 64-bit.

So my question is that is there any way these drivers will work on a 64-bit 8.04?

---

### Post by inportb on 2008-05-13
Hm, I'm interested too. Some 32-bit apps have 64-bit wrappers. Can one have the same for kernel modules?

---

### Post by Dinchamion on 2008-05-14
> **inportb said:**
> Hm, I'm interested too. Some 32-bit apps have 64-bit wrappers. Can one have the same for kernel modules?

I'm not sure, but my card worked pretty much out-of-the box with 7.10 and up (had to disable the Atheros HAL restricted driver first though). With 8.04, I got a new entry in the restricted driver list (support for Atheros I think, I'm back to Gentoo now due to other problems and a huge performance loss in Hardy, so I can't check -- something like that), but still worked.

I'm guessing it's madwifi drivers included in Ubuntu or something. Someone correct me if I'm wrong.

So, if you have an Atheros-based card, chances are it'll work, I don't think I just got lucky, since I never do. :D

---

