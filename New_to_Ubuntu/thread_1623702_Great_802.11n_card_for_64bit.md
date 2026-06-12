---
title: "Great 802.11n card for 64bit?"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by Tagged on 2010-11-16
Hey all!

I tried Ubuntu a couple of years ago, could not get my wifi working on my laptop at the time after many hours of trying so gave up.

Came back a couple weeks ago and 10.10 works great on my Dell 1525!!  Loving it!

Just bought my wife a new computer (dell Studio XPS 7100, AMD Athlon(i think) II X4, 4GB DDR3 1333 ram).  

I want to put 10.10 64 bit on her computer to take advantage of all 4GB of ram.  I need to order her a wireless card and would love to get one that works out of the box with 10.10 64bit.  Any recommendations?

Thanks all!!!

---

### Post by 3rdalbum on 2010-11-16
It's not quite "out-of-the-box", but I have an ALFA AWUS050NH that works with Ubuntu when you blacklist "rt2800usb" (add the line "blacklist rt2800usb" to the end of the /etc/modprobe.d/blacklist.conf file).

It's a draft-N device with a big antenna.

Hopefully in the future the need for blacklisting will subside.

---

### Post by Gone fishing on 2010-11-17
Recently I've found most cards just work or work with restricted drivers. I think all the dlink and gigabyte cards I've put in to a box were no problem.

My current card uses an Atheros chip-set and works fine I've generally found all older realtek chipsets to work straight out of the box. So I wouldn't worry or go to the shop and Google the card to see if there is a problem

here's a link [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

---

### Post by walt.smith1960 on 2010-11-17
I was looking for a wireless N adapter and bought  a Netgear WNA1100 USB adapter.  It was not recognized out-of-box but downloading and running this .deb file got it to work nicely.
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)  
The adapter has worked flawlessly wih Lucid & Maverick 64 bit  including suspend & resume. This is a 2.4 ghz/150 mb. device, not dual frequency if that matters.

---

