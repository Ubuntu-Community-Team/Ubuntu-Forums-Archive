---
title: "Any one having problems with the Turion II?"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by wjwoods184 on 2010-05-16
So i'm new to the whole linux thing, honestly. Just started reading about it in computer class and it sounds interesting, so i intend to try it out. Since I can't put it on the computer that i use now, it belongs to my dad, and he freaks out whenever i get near it, I was going to buy a new laptop that I could try it out on. I was just wondering if anyone had an AMD Turion II for their laptop, and ho well it worked with ubuntu. If it turns out its not gonna work out, i was goning to get a laptop with an i5.

---

### Post by QIII on 2010-05-16
That processor will work fine.

It might be worth you while to give us the rest of the specs on the machine so we can take a look at hardware compatibility.  There are relatively few problematic areas, but once in a while something can be troublesome and require a bit of adjustment.

---

### Post by wjwoods184 on 2010-05-16
AMD Turion II M500, 4 gb DDR2, 320 GB HDD (doesn't specify manufacturer), ATI Mobility Radeon HD 4570 w/ dedicated 512 mb. Thanks for the quick reply, not used to not having to call up a customer service line to get answers, thought a reply to my question would take longer.

---

### Post by tom.swartz07 on 2010-05-17
You will definitely run into problems with the graphics card.
ATI is absolutely terrible with support for linux users- they dropped support for my video card 3 months after it was released.



If youre really in the market for a new computer, definitely go for the intel i5's. I have a few friends that just got new ones and they are so redic fast, you wouldnt believe. Absolutely no problems with Ubuntu on them either. :P

---

### Post by alphacrucis2 on 2010-05-17
> **tom.swartz07 said:**
> You will definitely run into problems with the graphics card.
ATI is absolutely terrible with support for linux users- they dropped support for my video card 3 months after it was released.



If youre really in the market for a new computer, definitely go for the intel i5's. I have a few friends that just got new ones and they are so redic fast, you wouldnt believe. Absolutely no problems with Ubuntu on them either. :P

Quite wrong in this case. That HD 4570 is fully supported by the current Catalyst driver. When you first install it, Ubuntu will be using the Open source radeon driver, which will do most things ok. If you want to use ATI's Catalyst driver, then just select System - Administration - Hardware Drivers and it should give you the option of installing the Catalyst driver. The main advantage of the Catalyst driver is 3D performance and GPU power management. If you want to use it with Compiz desktop effects you will also need to install the "backclear patch" from here (this fixes an Xorg issue with slow restoring of minimised windows):

 [https://launchpad.net/~bryceharrington/+archive/violet](https://launchpad.net/~bryceharrington/+archive/violet)

---

### Post by wjwoods184 on 2010-05-17
Thank you all for taking the time to answer a newbie's question. This is the most helpful forum i have ever been to!  Might just have to save an extra week and get the i5 it looks like, from what i hear, the laptop I was origanlly was going to buy has a defective screen :(.

---

### Post by tom.swartz07 on 2010-05-17
> **alphacrucis2 said:**
> Quite wrong in this case. That HD 4570 is fully supported by the current Catalyst driver. When you first install it, Ubuntu will be using the Open source radeon driver, which will do most things ok. If you want to use ATI's Catalyst driver, then just select System - Administration - Hardware Drivers and it should give you the option of installing the Catalyst driver. The main advantage of the Catalyst driver is 3D performance and GPU power management. If you want to use it with Compiz desktop effects you will also need to install the "backclear patch" from here (this fixes an Xorg issue with slow restoring of minimised windows):

 [https://launchpad.net/~bryceharrington/+archive/violet](https://launchpad.net/~bryceharrington/+archive/violet)

My mistake, I had this card confused for an older gen version.

Still, you must agree with me that ATI has poor support for their video cards on Linux, correct?

---

### Post by alphacrucis2 on 2010-05-17
> **tom.swartz07 said:**
> My mistake, I had this card confused for an older gen version.

Still, you must agree with me that ATI has poor support for their video cards on Linux, correct?

Well they have released the details of their cards that the opensource devs need to build high performance opensource drivers. Also the Catalyst linux driver has been continuously improving since I started using it on my hd3400 (yeah it would be annoying if you had one of the cards they dropped support for last march but they dropped Windows support as well not just Linux). If you were running Windows with one of those older cards then there's no more driver updates for them either. You notice it more in Linux because of the short release cycle means that the new versions of Xorg and kernel render the pre March 2009 Catalyst driver incompatible with the newer Linux versions. The good news is that the OSS driver support of the old cards is getting better.

---

### Post by LowSky on 2010-05-17
> **tom.swartz07 said:**
> My mistake, I had this card confused for an older gen version.

Still, you must agree with me that ATI has poor support for their video cards on Linux, correct?

Actually I can't agree. AMD/ATI support is only getting better. Yes they stopped support on anything older than than the HD series of video cards, but lets be fair, at some point you have to draw a line on how long you intend to support equipment. It isn't fair for a company to have to produce new drivers for every kernel upgrade for products they don't sell or warrant.

---

### Post by QIII on 2010-05-17
When ATI was bought by AMD in 2007, AMD made a commitment to making their drivers work with Linux.  That was an absolute.

It took them a while, but they are there now.

Yes, the "legacied" some older cards.  So did nVidia.  Both got such nasty feedback that they created legacy drivers.  Those drivers are not as good, of course, but will suffice.  Older cards from either OEM can still be used with the open source drivers.

If you really want to understand AMD/ATI's commitment, consider the fact that for the last several new releases of Ubuntu, AMD/ATI has done a lot of work to make sure that their latest drivers work and are available in the repositories at the final release date.

---

