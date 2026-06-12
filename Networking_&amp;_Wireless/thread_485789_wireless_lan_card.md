---
title: "wireless lan card"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by krysia on 2007-06-27
I have just bought a wireless pcmcia card through ebay (edup iee802.11g) the 
install disc that came with it only works on windows !! is it possible to load the 
device by using wine or some other driver,or is it going to be a wasted purchase.
help appreciated.
krysia.

---

### Post by kevdog on 2007-06-27
I can tell you havent really done any reading on the forums to answer your question.  It really depends on the chipset of the card.  Depending on whether this is a card or usb device, you can find your chipset by booting with the card or usb stick in the correct slot and then typing at the command line:
lspci
of
lsusb

---

### Post by bethnesbitt on 2008-02-08
I bought the same card as well, and I cannot get it to read in ubuntu no matter what I do.  It reads in windows, but in windows when you install the driver, the pc freezes.  I am using ubuntu amd64 and it doen't show anything.

Yes I have used ndiswrapper, madwifi, linux restricted modules (all of them).  I even downloaded a linux driver for it from sourceforge.  Does anybody have any other ideas?  am I missing a step?

Everywhere I read I see these same posts, and then nobody either responds or the person says yay i got it to work, but how...........!!!!

---

