---
title: "ISA Network Card"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by twistie on 2007-07-02
Okay,
I'm running Fiesty on an old P3 with an Asus CUV4X motherboard. The only problem is despite the ample space for a PCI network card, I don't have one and I havn't got the money to go and buy one (well I do but I like a challenge). Instead I have an old ISA card. Its a D-link DE-220P Rev A2 which is of coarse plugged into the one and only ISA slot on the motherboard. I've tried the good old "sudo modprobe ne" but that doesn't work so I try manually configuring some modprobe overrides (specifically irq and io) it but when I go to find the device IO using PNPdump I find that ISAPNPTools isn't integrated into the Distro and when I go to download it also seems that nobody even serves the package anymore. 

So can anyone else suggest a way that I can get this card to work?


Thanx in Advance!

---

### Post by kevdog on 2007-07-02
I wish you luck -- but I think I read somewhere that ISA cards are not supported.  Im sure there is a workaround.  As far as not having enough money for a PCI card, I highly doubt that!!! They are selling on Craig's list in some cases as low as $5.  I bought one a year ago on sale from BestBuy for $10.  ;)

---

### Post by twistie on 2007-07-02
Well the big problem is that I'm a minor (under 18 ) so I don't have a credit card + all the nearby computer shops are close to impossible to get to!

---

### Post by kevdog on 2007-07-02
Hey Ive been to Townsville Australia.  It was a great place to visit.  I dont know the stores there real well, but I can sympathize.  They probably dont have too many computer stores!  Isnt this time of year the WWII celebration coming up?

---

### Post by twistie on 2007-07-02
No, we only have those in special years... normally every 5 or 10 years.

---

### Post by kevdog on 2007-07-02
I didnt know that.  I caught the one a year and a half ago.  It was great!

---

### Post by twistie on 2007-07-02
Yer, they are... I think its more of a celebration here because Townsville seemed impenetrable to the locals during the war. We had the largest overseas deployment of the US army here and the first Japanese air raid on the city, which lasted 2 hours, only managed to damage a palm tree on the beach front.

EDIT: Stole a PCI Ethernet from a friend who is using wireless card. But it would still be nice to know

---

