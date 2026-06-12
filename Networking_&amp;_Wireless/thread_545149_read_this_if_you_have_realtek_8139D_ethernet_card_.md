---
title: "read this if you have realtek 8139D ethernet card and it doesn't work in ubuntu"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by trooper666 on 2007-09-07
If you have this card and you dualboot with windows and your card doesn't work in ubuntu try this test:

turn off your computer then switch off its power either by the PSU switch or unplugging the power cord, wait a few seconds then turn it on again and boot straight into ubuntu

if your card starts working now you have the same problem as it was described with some realtek 8169 (can't find the thread now) cards, apparently when you exit windows the card is put in some sort of power saving mode that the linux driver can't wake it up from

hopefully kernel developers will fix this soon

but atleast i could update ubuntu now

---

### Post by noob12 on 2007-09-07
Probably you mean this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

If more folks can confirm this, I'll add notes there that it applies to the 8139 as well.

---

### Post by Zigger on 2007-09-09
> **trooper666 said:**
> If you have this card and you dualboot with windows and your card doesn't work in ubuntu try this test:

turn off your computer then switch off its power either by the PSU switch or unplugging the power cord, wait a few seconds then turn it on again and boot straight into ubuntu

if your card starts working now you have the same problem as it was described with some realtek 8169 (can't find the thread now) cards, apparently when you exit windows the card is put in some sort of power saving mode that the linux driver can't wake it up from

hopefully kernel developers will fix this soon

but atleast i could update ubuntu now

I'll probably be banned or whatever for this post.


But Is This The Trooper 666 who played Robot rage?
If it Is,PLEASE,get in contact with me,Me and spike want to know if you're alright.

---

### Post by trooper666 on 2007-09-10
> **noob12 said:**
> Probably you mean this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

If more folks can confirm this, I'll add notes there that it applies to the 8139 as well.

im surprised no one else replied to this 8139 is a very common nic...

---

### Post by noob12 on 2007-09-10
I went ahead and put a note on the thread saying that it had been reported to work for 8139 cards as well, but I'll make a stronger statement there if I hear more confirmation.

---

