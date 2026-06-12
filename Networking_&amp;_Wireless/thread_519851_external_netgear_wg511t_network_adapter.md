---
title: "external netgear wg511t network adapter"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by hellz12 on 2007-08-07
I've come to the conclusion that my internal network adapter (BCM 4318 AirForce One 54g) will not work with Ubuntu (7.04), so I decided to get a Netgear WG511T external PCMCIA network card. What I need to know is what to do next, the card obviously does not light up when I boot into Ubuntu so I figure I'll need to use ndiswrapper to use the drivers on the CD that came with the card, could anyone give me some resources on how to go about this? I've searched all over the forums for using an external Netgear WG511T PCMCIA network card and nothing was found. Thanks.

I'm currently dual booting Windows XP and Ubuntu 7.04.

PS. I'm not sure if Ubuntu recognizes the PCMCIA card (Netgear) or not...

---

### Post by solar george on 2007-08-08
Hi,

I have a BCM43?? card and used (i think) this post ([http://ubuntuforums.org/showthread.php?t=190177&highlight=bcm+43xx](http://ubuntuforums.org/showthread.php?t=190177&highlight=bcm+43xx)) to get it to work.

For the pcmica card post the results of lspci.

---

