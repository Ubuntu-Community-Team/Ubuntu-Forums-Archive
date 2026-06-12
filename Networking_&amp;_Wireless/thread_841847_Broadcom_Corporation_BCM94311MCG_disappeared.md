---
title: "Broadcom Corporation BCM94311MCG disappeared?"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by TeeAhr1 on 2008-06-26
Well, that's odd. I've got an HP Paviolion dv2000 with a Broadcom Corporation BCM94311MCG card, which I enabled through the Restricted Drivers manager without an issue yesterday, came right up, good signal, no problems. Today, however, it's just gone. It's not even showing up in lspci. Can anyone give me some ideas on how to start troubleshooting this? I've never had a network card just disappear like that.

thx-
p.

---

### Post by ajmorris on 2008-06-26
Not showing up in lscpi?? oh dear... This *could* mean that the card has died... or it might just mean that for some reason, the laptop is not giving the card power, so as far as lspci is concerned, it doesnt exist... Not really sure where you would start troubleshooting this, happened to me a while back on my BCM4311 ... I had to buy a new card... Although, this error could be an incorrectly configured kernel, or BIOS...


AJ

---

### Post by Ayuthia on 2008-06-26
You might check this link:
[http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013)

There are some HP laptops that are having problems with the wireless card not being recognized.  If yours is in this category, then you can contact HP and get it fixed.  Mine had the same problem and I was unable to see my wireless card in any operating system I had installed on there.

The link does say that the problem might not be the wireless card, but the motherboard itself.

---

### Post by TeeAhr1 on 2008-06-27
Ayuthia, you are a lifesaver! Updating the bios totally did the trick. Thx a million!

---

