---
title: "ttyACM0 USB modem lost?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by CaptBry on 2009-03-03
It was all going so well!

Then one boot-up, when i clicked on the toolbar Network Connect dualPC icon, a window pops up and asks for a network password.
Ubuntu 8.10 never did this before and my Windoze virus paranoia reflex clicked DENY. 
Turns out it was a problem on Verizon's side of the USB Broadband modem connection. OK I got them PAID LOL!

but now the "Network Is Disconnected" message won't go away, no dualPC Icon shows up, and my PEERS CHATSCRIPTS PROVIDER files are as when they were working.

Please, what are ALL the steps, links, configurations, Ubuntu needs to reach ttyACM0 as a modem?

Thanks in advance!

Bry

---

### Post by reid8.1 on 2009-03-05
hey Cap,you said you had a connection and then lost it, I don't think I can help you with that but perhaps you can help me. I am trying to connect to earthlink with a dial up and have the same tty (ACM0) modem displayed. my problem is that I seem to connect and then disconnect repetedly. if you could be so kind, I have posted my wvdial.conf under 'usb modem blues' and I thought there maybe something in your .conf that may help me. thx Reid.

---

### Post by CaptBry on 2009-03-05
QUOTE-problem is that I seem to connect and then disconnect repetedly. (sic)

I have heard of that prob in my Searches to get reconnected.

In Admin-Network there is a box to click " reconnect automatically" that might get your OFF back to ON (maybe to be OFF again in an infinite loop?)

my ATM0 uses /peers/provider and /chatscripts/provider.
Not wvdial.conf. Even when it was working. unless i'm wrong, of course! LOL!

I KNOW others are having your issue, keep Searching, you'll get it!

cheers,
CaptBry

---

### Post by CaptBry on 2009-03-13
Well, thank you for reading.

i'm STILL using MS 'cause it can deal with a USB modem.

---

### Post by CaptBry on 2010-04-15
Got it.

Verizon's modem needs to be periodically 'updated' by its winblows-ware program. So every few days it goes slow or wacky and I have to let its winblows program re-update it. I have dual-boot so its easy. But being a USB modem, I'm sure you can plug it into any wintell PC and get it updated.

vw.conf and Gppp solved my issues - note gppp looses the tty/ACM0 connection if I plug the modem into a different USB port. FYI

---

