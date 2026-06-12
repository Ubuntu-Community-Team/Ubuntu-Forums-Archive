---
title: "hello, help please"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by Ribby on 2007-08-25
sorry to bother you all, i recently got ubuntu 7.04 Feisty im new to ubuntu if you cant tell lol.

anyway i have a belkin wireless dongle model f5d7050 but ubuntu isntrecognizing it, how would i get it on my computer and working?

ive tried this ndiswraper but i think im going wrong with it.

now i'm on a laptop with windows on so if theres any replys / help i can come on here and mess with ubuntu, ive now been trying get it to work for 4 days 11 hours something like that lol... i'm like the terminator refuse to give in :P 

any help, thanks.

---

### Post by ddrichardson on 2007-08-26
Start [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"). Post any problems and let us know.

---

### Post by babysteps on 2007-08-26
> **Ribby said:**
> sorry to bother you all, i recently got ubuntu 7.04 Feisty im new to ubuntu if you cant tell lol.

anyway i have a belkin wireless dongle model f5d7050 but ubuntu isntrecognizing it, how would i get it on my computer and working?

ive tried this ndiswraper but i think im going wrong with it.

now i'm on a laptop with windows on so if theres any replys / help i can come on here and mess with ubuntu, ive now been trying get it to work for 4 days 11 hours something like that lol... i'm like the terminator refuse to give in :P 

any help, thanks.

The Belkin wireless f5d7050 can be many things! You might have your work cut out for you.  
Many of us have that USB stick.So, the good news is, there is a lot of info out there.  The bad news is, you need to first find out what version and what chipset your particular one has.

You might start with plugging in the usb stick, and going to the Terminal and type:
lsusb 

and post that here.

Also, what do you get when you type:
lsmod |grep usb

From those two you'll have a better lead on how to proceed.

Babysteps

---

