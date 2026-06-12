---
title: "[SOLVED] Which wireless is best"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by forestpixie on 2007-05-15
Hi i'm a bit new at this Linux stuff and can't help noticing wireless problems seem to abound.

I've looked at the which wireless sticky but still not too sure

I'll be building a new PC for my son and it's gonna have Ubuntu from the get go - he'll be needing wireless for it.

I have a Netgear DG834G which has given me no problems at all - would i be best served getting a netgear card?

The sticky has 2 which are known to work on Feisty but they're both pcmia - has anyone got a pointer for me.

And also when I do his installation it will at that point have a direct connection while I'm making sure it's got updates and apps he'll be needing.

Once the install is done it'll lose it's direct wired connection - will that foul me up when I get round to his wireless setup

Bit rambling - sorry for that

TIA

---

### Post by x64Jimbo on 2007-05-15
When you're looking for cards, you only need to know one thing: the chipset. Look specifically for Atheros and Intel based cards, and stay away from Broadcom cards. The brand makes absolutely no difference. If it's a desktop, I suggest using one of the PCI cards that you insert into the motherboard - they have external antennas and can be easily positioned for maximum signal strength. 
For the chipset the card uses, you may need to Google the model number followed by the word "chipset."

---

### Post by jml on 2007-05-15
To answer the second part of your question.  There should be no problem doing the install with a wired connection.  If the computer in connected to your network before the install begins, the installer should detect your card and after answering a few questions should have it running as soon as the install is completed.  After you run update manager and install the extra stuff you want your son to have, you can then disable the wired connection and configure the wireless connection.  And I completely agree with x65Jimbo.  It took me nearly a year to get a Broadcom card working in a Debian based setup.  Atheros and Intel based cards are much easier to work with.  And the PCI cards seem to be better than USB based solutions.  I have never been able to get one of those to work.  Good luck on your project.

Joe

---

### Post by joe.turion64x2 on 2007-05-15
Definetely get an Atheros card if you can, they are far superior to Intel's in the same price range.

---

### Post by forestpixie on 2007-05-15
thanks everyone - advice much appreciated and will be heeded 

with any luck i won't be back later in the month looking for answers and help

a little planning can go a long way

---

