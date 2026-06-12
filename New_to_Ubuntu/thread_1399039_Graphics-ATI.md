---
title: "Graphics-ATI"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by JakeFrederix on 2010-02-05
I recently purchased Acer Aspire 5542, this comes with an ATI graphics card.
This apparently does not go down well with Ubuntu. The standard games (eg gnometris) tend to have terrible graphics, or simply display part of the background in their frame.
I have tried it both with, and without the proprietary driver.
Anyone got any suggestions?

Kind regards,
Jake

---

### Post by verachion on 2010-02-05
> **JakeFrederix said:**
> I recently purchased Acer Aspire 5542, this comes with an ATI graphics card.
This apparently does not go down well with Ubuntu. The standard games (eg gnometris) tend to have terrible graphics, or simply display part of the background in their frame.
I have tried it both with, and without the proprietary driver.
Anyone got any suggestions?

Kind regards,
Jake

Have you tried the ATI catalyst control centre? I am running an ATI card and after you install it, it allows you to enter in to 3D. I can't remember where it is try **ubuntu software centre**

---

### Post by JakeFrederix on 2010-02-05
Yes, I found the settings. But what on earth do I have to change?
Absolute n00b when it concerns graphics...

---

### Post by tsouza on 2010-02-11
> **verachion said:**
> Have you tried the ATI catalyst control centre? I am running an ATI card and after you install it, it allows you to enter in to 3D. I can't remember where it is try **ubuntu software centre**

I guess he thinks you're talking about general graphics quality. When indeed you're talking about buggy graphics, I suppose. If this is the case, I can only tell you that ati linux driver sux hell and I have this kinda problems too... hope amd put better efforts in linux driver some day...

Regards,
Thiago Souza

---

### Post by Mark Phelps on 2010-02-11
Aspire's come in different models -- some with integrated graphics, some with graphics cards.

Open a terminal and do "lspci" to see a list of devices.  Somewhere in that list you will see an entry for your video device.

Report back here what you find.

BTW, if you're running ATI and it's not one of the newer HD 3x/4x/5x series, there will be no ATI driver that you can use.  ATI dropped Linux support for the "older" cards last May.

---

### Post by sandyd on 2010-02-11
its a 4200

---

### Post by sandyd on 2010-02-11
if your having problems with the ubuntu-supplied driver, try removing it and installing the one from ATI's site.

---

