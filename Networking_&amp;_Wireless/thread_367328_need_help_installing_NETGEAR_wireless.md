---
title: "need help installing NETGEAR wireless"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by gamegary on 2007-02-22
greetings all, I am running Ubuntu 6.10 and am trying to install drivers for my netgear wireless N PCI adapter.  (WN311T)

The bos says it should run on Linux, but the disc it came with does not have any drivers that are formatted for linux, only .exe.  :mad: 

So please, if anybody could help me with this problem, it would be much appriciated, and if not, then I suppose i will have to shift back into the hands of the evil microsoft windows. 

greatest of regards,
        Gary Lohkamp

---

### Post by gradedcheese on 2007-02-22
alright, plug the card in and we'll see what happens.  once you've plugged it in, wait a few seconds and then open the terminal (Applications->Accessories->Terminal).  Now type "lspci" and press Enter.  Post any lines starting with "Ethernet Controller" here.  Also run "iwconfig" and post its output here.

---

### Post by chewearn on 2007-02-22
Hot plug a PCI card?!  Is that wise?

Shutdown, ground yourself by touching the PC case, unplug the power cord.  Then open the case, and plug in the card.

---

### Post by gradedcheese on 2007-02-22
oops :) It's late here and I misread and thought he said PCMCIA...

---

### Post by gamegary on 2007-02-24
when i put in lspci, this is what popped up that requested me to show:

02:09.0  Ethernet Controller:  Marvel Technology Group Ltd.  Unknown device 2a02

and when I put in iwconfig, this is what it gave me:

lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

I hope this is as useful as you had hoped it would be =]
and thank you for responding    :)

---

### Post by gradedcheese on 2007-02-24
Ah, Marvell :(  The only way (for now) to get that one working is to use ndiswrapper.  There are some ndiswrapper/ubuntu guides online (and on this forum).  It's going to involve extracting your Windows driver and installing ndiswrapper, but it's not terribly difficult to do.  So, set aside some time, locate a how-to guide, and go for it :)

---

### Post by gamegary on 2007-02-24
Alright thanks =]

Could you perhaps post a link to one of these tutorials? That would be quite helpful and much appriciated

---

