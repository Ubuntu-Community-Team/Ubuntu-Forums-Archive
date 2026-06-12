---
title: "I Installed ndiswrapper and now Ubuntu won't boot"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by portach king on 2008-04-25
Hi,
I posted a thread regarding this on the General help page but it's getting no attention there.
I have a broadcom (4318 ) card, I tried b43 but it didn't work out so well (it did at first but the quality deteriorated so much that it wont even connect anymore). So as a last resort I decided to try ndiswrapper. 
I'm living to regret that decision.
Ever since installing the driver and restarting the computer Ubuntu won't boot. I get a black screen after the splash screen.

I really to need to get this amended urgently as I have an essay I need to be working on for college. Right now I have no access to my computer.
I'm using the live cd to write this, I thought I would be able to use the live cd to recover my documents from the hd and place them onto my external hd, but it's not giving me the permission to do so...
Please, please help.

---

### Post by ToM-X on 2008-04-25
Boot into Ubuntu Recovery at boot and login then:

sudo apt-get remove ndiswrapper

then reboot with:

sudo init 6

---

### Post by mikko109 on 2008-04-25
i have broadcom 4318 on my Acer Aspire 5045WLMi and i am afraid of install ubuntu becouse i cant get this card to work on live cd :(

---

### Post by portach king on 2008-04-25
First of all, ToM-X... Thank you!!
I was pulling my hair out, I thought I'd lost a 2,000 word draft of an essay I was getting finished.

Mikko109, I think my card is broken or faulty, as many others are not having the same sort of dramatic trouble that I am.

---

