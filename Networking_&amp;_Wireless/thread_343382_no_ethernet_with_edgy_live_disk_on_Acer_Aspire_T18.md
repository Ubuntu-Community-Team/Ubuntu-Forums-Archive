---
title: "no ethernet with edgy live disk on Acer Aspire T180"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by paul cooke on 2007-01-21
Hi, I'm about to install Ubuntu edgy onto an ACER Aspire T180 with integrated gigabit LAN... I tried the live disk first and found the ethernet never comes up, the lights on the back and on the switch just remain off. Latest Knoppix however has no trouble finding and configuring it.

The device info given by Knoppix is:
Marvell Technology Group Ltd. Unknown device 4364

I understand that this beast is a problem and someone has managed to get ethernet up but had to compile a custom kernel. 

I am in no mood to do this... is it working in Feisty?  

I'm going to try Dapper on it for now and will get back with an update once I've finished pulling down a dapper iso and tried it out.

---

### Post by paul cooke on 2007-01-21
> **paul cooke said:**
> Hi, I'm about to install Ubuntu edgy onto an ACER Aspire T180 with integrated gigabit LAN... I tried the live disk first and found the ethernet never comes up, the lights on the back and on the switch just remain off. Latest Knoppix however has no trouble finding and configuring it.

The device info given by Knoppix is:
Marvell Technology Group Ltd. Unknown device 4364

I understand that this beast is a problem and someone has managed to get ethernet up but had to compile a custom kernel. 

I am in no mood to do this... is it working in Feisty?  

I'm going to try Dapper on it for now and will get back with an update once I've finished pulling down a dapper iso and tried it out.

Dapper gave me a kernel panic with the live DVD... :(

Feisty Fawn desktop live CD daily build dated 2007/01/21 works with it (I'm posting this from it). I've just used the hardware database tool to send this machine's details in to the database.

So I can look forward to having Ubuntu on this machine in April when Feisty gets properly released. I can't trust it yet on this box.

---

### Post by harro on 2007-02-09
I have recently bought a AcerAspire T180 and I have the same problem. When bootting from the 6.10 CD the network adapter and soundcard (both onboard) are not recognized/utilized.

If I was to use the 7.04 Herd 3 CD. I wonder if it would work, but more importantly, would I be able to update my installation just as if it was a regular, stable, distribution? Would it be possible to just update to the stable 7.04 once it is released in April without having to re-install?

---

### Post by paul cooke on 2007-02-09
> **harro said:**
> I have recently bought a AcerAspire T180 and I have the same problem. When bootting from the 6.10 CD the network adapter and soundcard (both onboard) are not recognized/utilized.

If I was to use the 7.04 Herd 3 CD. I wonder if it would work, but more importantly, would I be able to update my installation just as if it was a regular, stable, distribution? Would it be possible to just update to the stable 7.04 once it is released in April without having to re-install?

Yes: that's precisely what you end up with if you keep doing the updates. :) you will have Feisty Fawn on release date...

wow, that's you're first ever bean... welcome to the community. Hope you have fun.  Cheers

---

### Post by skyhopper88 on 2007-02-10
I have a similar problem with a T160. My ethernet is recognized, but I cannot set my connection to full duplex no matter what I do so it's super slow. I've tried on 6.06 and 6.10, both LiveCD and with them installed. I'm wondering if I should try Fiesty Fawn, it IS alpha after all.

---

### Post by harro on 2007-02-11
> **paul cooke said:**
> Yes: that's precisely what you end up with if you keep doing the updates. :) you will have Feisty Fawn on release date...

wow, that's you're first ever bean... welcome to the community. Hope you have fun.  Cheers
Thanks for the welcome and the confirmation about updating Feisty!
As a matter of fact, I am writing this from the booted live cd Feisty Fawn Herd 3!
Both the soundcard and the network adapter work. I think I'll go ahead and install...
.

---

