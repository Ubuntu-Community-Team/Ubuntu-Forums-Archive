---
title: "Dial-Up help"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by {{DoX}} on 2008-05-11
Note: all lines enclosed in {}'s are lines entered into terminal etc.

Hey everyone im a total n00b when it comes to linux in general but either way im here asking for help.

I have got a 700 Mhz IBM Thinkpad T20 Laptop and I put Ubuntu 8.05 Hardy Heron distro on it

Im on dial up internet and went through a lot of trouble trying to get this bugger to dial thus far this is what I have done:

Started out hoping maybe ubuntu had the drivers for the modem so I fired up the terminal and typed { sudo wvdialconf /etc/wvdial.conf } It asked for admin pass I entered it and it returned no modem found..

Next I went and got a program scanModem and extracted and ran it from the terminal. Went to the ModemData.txt generated from the program. It determined that I had a Xircom Mini-PCI V.90 56k Modem and said I could get drivers from [http://linmodems.technion.ac.il/pack...l-2.6/martian/](http://linmodems.technion.ac.il/pack...l-2.6/martian/)
It also said something about using martian-full-20071011.tar.gz
So I did

Downloaded the file put it on my USB moved it to the lappy. looking at the install text document it says

=====================
building
=====================

In root directory run
$ make all


=====================
Installation
=====================
in root directory run
$ su
$ make install



Where did I go wrong? Where do I go from here? Do I even have the right drivers? Are they even drivers?

---

### Post by {{DoX}} on 2008-05-11
Wow.. Really no one has as any info or help for me? I got more feedback on overclock.net, come on guys!

---

