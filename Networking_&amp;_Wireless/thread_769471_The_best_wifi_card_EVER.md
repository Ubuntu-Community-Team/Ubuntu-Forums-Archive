---
title: "The best wifi card EVER?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by bvongunten on 2008-04-26
Hey all!

I have been wrestling with wireless on Linux for the last six months.

I have an Asus mobo with one of those ridiculous onboard USB wifi adapters which uses the RTL8187 chipset. I gave up on that particularly unsavory lump of garbage a LONG time ago. I found an RT2500 based PCI card at a flea market for 5 bucks... Popped that in and it did work (once I turned off Network Manager), the problem is that it is incredibly unstable. I am not sure why, but sometimes it will work flawlessly for hours and other times it will run for five minutes and then just stop working, sometimes it never even gets a DHCP lease sucessfully and just decides to start napping. I have gotten really good at issuing the following command:

root@hypothalamus:~# /etc/init.d/networking restart

I have to say that issuing this command ten to twenty times a day is getting old. All I use for encryption is WEP... It really is quite pathetic; I feel forced to keep my expectations low...I haven't even tried WPA for fear of making a bad situation worse...


Now I will get right to the point: Given my experiences up to now I would like my next Wifi purchase to be much less painful. I have honestly given up on both of the Wifi cards that I have installed right now...

What Wifi card JUST WORKS? Just install, boot and configure with network manager (or whatever)? Which is the BEST Wireless card for use with ubuntu? I dont need draft-n, my router only supports G and that is all I want or need.

Please, tell me what has worked for you...without jumping through hoops?


Thanks,

BvG

---

### Post by Monicker on 2008-04-26
Netgear WG511T.  Worked right out of the box with the madwifi drivers that are included with Ubuntu.  I haven't had any problems with it at all.


Dunno what country you are in, but I also have this card:

[http://www.airlink101.com/products/awlc4030.html](http://www.airlink101.com/products/awlc4030.html)

I got it for about $20 at Fry's.  Also works fine with Ubuntu.

---

### Post by doorknob60 on 2008-04-27
> **Monicker said:**
> Netgear WG511T.  Worked right out of the box with the madwifi drivers that are included with Ubuntu.  I haven't had any problems with it at all.


Dunno what country you are in, but I also have this card:

[http://www.airlink101.com/products/awlc4030.html](http://www.airlink101.com/products/awlc4030.html)

I got it for about $20 at Fry's.  Also works fine with Ubuntu.

I just got one of these today, coincidentally, and it works great. Mine was $70 though :P

---

### Post by bvongunten on 2008-04-27
Could either of you tell me what chipset is used in that particular model? Is it USB or pci(x)? Does it work at 54mbit speeds?

I ask because I live in Switzerland, and while I may not be able to easily find the *exact* card you mentioned, I may be able to find one with the same chipset, and thus drivers... ;)

thanks!

BvG

---

### Post by bvongunten on 2008-04-27
Ohh and BTW this is for a desktop pc, so PCMCIA would not really work... :(

---

### Post by bvongunten on 2008-04-27
Ok, checked out the link in the above post, aqnd browsed around the site and found this other card there:

[http://www.airlink101.com/products/awlh5026.html](http://www.airlink101.com/products/awlh5026.html)

The card you two say that you use has the Atheros chipset, which I presume works particularly well/ is well supported in Linux and specifically Ubuntu. 

The question is whether the awlh5026 uses the Atheros chipset as well?

Presumably yes, but??

---

