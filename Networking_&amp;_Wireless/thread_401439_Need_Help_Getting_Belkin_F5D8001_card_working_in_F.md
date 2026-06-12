---
title: "Need Help Getting Belkin F5D8001 card working in Feisty"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by samuraiswordsman on 2007-04-04
Can someone help walk me through on getting my Belkin F5D8001 working in Feisty?
I've already tried countless times in Edgy, and got discouraged and gave up..
I followed many different methods, and ndiswrapper just keeps screwing up and not recognizing my card... hopefully, if someone can give me a hand and make some sense of this, it might work this time...
Please help me... :( :confused:

---

### Post by medley on 2007-04-04
> **samuraiswordsman said:**
> Can someone help walk me through on getting my Belkin F5D8001 working in Feisty?
I've already tried countless times in Edgy, and got discouraged and gave up..
I followed many different methods, and ndiswrapper just keeps screwing up and not recognizing my card... hopefully, if someone can give me a hand and make some sense of this, it might work this time...
Please help me... :( :confused:

Good luck to you. I've had a message posted for wireless help that's been viewed 62 times so far with not one response. It seems getting wireless working is not only challenging in ubuntu but also a mystery to the vast majority.

At least with efty and feisty.

---

### Post by samuraiswordsman on 2007-04-05
Wow...............
Well this sucks...:sad:

---

### Post by JasonCfirefox on 2007-04-06
Maybe that card is not supported at the moment I had to get a card that was supported. There is a list of supported cards in the netwoking & wireless section.

Im using a asus WL 138G V2 on feisty. i know how to get that card working but couldnt say about the others.

---

### Post by sol-lab on 2007-05-30
First post long time user, I've been reading the net for a while now and found that I have the same problem so here's my help. The (Ndiswrapper) supported is 1.22 only for this card. found the information here.. [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

Ndiswrapper 1.22 download [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=437275](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=437275)

LINE # 42
Card Name: Belkin F5D8001 N1 Wireless Desktop Card (rev 01)
  *Ndiswrapper version: 1.22
  *Chipset name: Athereos Communications, Inc. Unknown device 0023 (rev 01)
  *PCIID: 168c:0023 (rev 01)
  *Windows driver location: [http://www.belkin.com/support/article/?lid=en&pid=F5D8001&aid=5928&scid=0&fid=2587&fn=F5D8001v1_US_1.00.05_W2.exe](http://www.belkin.com/support/article/?lid=en&pid=F5D8001&aid=5928&scid=0&fid=2587&fn=F5D8001v1_US_1.00.05_W2.exe) 
extract with cabextract, unshield data1.cab, ndiswrapper -i Disk1/DriverXP2K/net5416.inf
  *Ubuntu 6.10 on a desktop machine, detected but sometimes cannot change essid to associate with an AP. try using “irqpoll” kernel option.

Currently using 7.04 and the card is not detected, the Updated Ndiswrapper 1.34 will hard freezes the machine so don't try installing with it. 

My problem is the compile! grrr so its still not working for myself either. Some help I hope

---

### Post by d3vino on 2007-08-26
Got my Belkin N1 F5D8001 card to work using the driver that came with it and using the notes at the following link to install it:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

I had issues with my Dell 1390 wi-fi card and figured the notes were very good and got me up and running.  With that I felt they were good enough to get me through this install too.  I followed his notes exactly except used the Belkin driver in it's place.  I also skipped the black list part since it didn't apply.

ndiswrapper 1.47
Driver: net5416.inf, net5416.cat, and ar5416.sys.  

Good luck!

---

### Post by smellycorpse on 2007-11-25
hey can you tell me what you did in place of step 4? i'm having some trouble with that part but i have the belkin driver (the net5416.inf, net5416.cat, and ar5416.sys)

---

