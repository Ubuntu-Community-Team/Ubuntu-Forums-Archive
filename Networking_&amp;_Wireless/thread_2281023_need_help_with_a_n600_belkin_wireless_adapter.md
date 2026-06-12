---
title: "need help with a n600 belkin wireless adapter"
date: 2015-06-03
forum: Networking &amp; Wireless
---

### Post by iamrandy on 2015-06-03
i have been doing research and trying diefferent methods to get this adapter to work, all to no avail. I have ubuntu 12.04 on a gateway amd 64. and the adapter is belkin n600 


thank you

---

### Post by iamrandy on 2015-06-14
so now i have upgraded to 14.04.2 and have found a few threads that have said solved and i've tried to use them to solve my problem and still no blue light.  if  anyone could please help i'd be very appreciative

---

### Post by Vladlenin5000 on 2015-06-14
When asking for help please avoid the vagueness of "trying diefferent methods to get this adapter to work, all to no avail" and describe what you did and the results instead. That said, I would normally follow with the usual "please check the stickies, especially the Before posting in Networking & Wireless one, where there are instruction on how to download an run a script that can give a lot of useful information about the hardware, drivers, settings, etc. but in this case it isn't worth the trouble:

Belkin n600 isn't supported for Linux and never will be. The only way to make it work used to be with ndiswrapper. Considering ndispwrapper is a last resort and NEVER worked acceptably for most of the hardware it was intended to "support" my suggestion is to forget about it once and for all. A new, fully supported, faster, more efficient and reliable WiFi dongle costs $10 or less. Enough said!

---

### Post by iamrandy on 2015-06-14
ok all very good information but i really think you might as well have called me stupid

thanks

---

### Post by Vladlenin5000 on 2015-06-14
Not my intention for sure... Actually I consider any attempts to keep using old hardware commendable. However, some things are objectively obsolete or at least superseded.
Your entire case boils down to how valuable is your time. I'm not even factoring in the time the volunteers here would have to dedicate to this "project" but the amount of feedback you received should be enough as an indication.

Different than most people here - who would simply ignore this and any other similar threads - I feel that some things should be said for the sake of the users asking for help. Call it reality check, brutal honesty, whatever... The fact remains: Some old hardware simply isn't worth the trouble and the time.

---

### Post by kurt18947 on 2015-06-15
I have learned when purchasing hardware to do a bit of research first. Buy hardware that is known to be supported and life is pretty simple. Buy hardware that is not supported and life can be pretty frustrating. USB wifi adapters known to work with linux distros are pretty inexpensive though they probably won't be the latest ac wonderstick.

---

### Post by chkneater on 2015-08-20
I totally agree with kurt... the comment WAS condescending and I am currently exeriencing the SAME probs as kurt.. and I have had this problem with EVERY single usb wireless adapter... it seems to me that these quickly released versions of Ubuntu don't support crap except a few select devices... almost like developers are working on the things they prefer rather than what people want... There are numberous threads with people having the e x a c t  s a m e THING!!!  And you would rather just tell someone "Ahh.. screw it and spend money till you find soomething that works.."  What is up wiht that???  It's gong to take manpower and time... hmmm Don't most things??  This is supposed to be volunteer based, but at least offer USEFUL advice rather than just throw it out... developers are able to get linux to run on their Commodores just for fun but can't get seemingly ANY wirelss adapter to work, Belkin and Broadcom... the two most popular and you claim there is ZERO support??   Maybe the resoponse should have said " Ok, well you have found a bug in thie software." And then reported OR ASKED the person to let Launchpad know (BTW, forward this issue to Launchpad.net and explain all that you've tried and the type of hardware like comp, adapter, etc... it may not help immediatelty but they will at least TRY to assist you..)   This is crap the way people wait on edge for an answer to an important problem and the best we can get is some guy saying that it's junk... it's not junk... there is support somewhere whether it's ndiswrapper or whatbit... did anyone ask what driver was being used?  Did anyone ask him for ifconfig?  I am so disappointed at this site from this response...   If you can't find the answer here, and I would wait and give some tiem, there are great Admins that really know their stuff, try just googling and also peruse Launchpad.net and other Linux based sites.   Ohh, and what does it say that a new distro (14.04) doestn't have backwards compatibility?  As long as I've used Ubuntu it was ALWAUS backwards compatible and getting  header upgrades didn't scare me back then.. NOW every new update totally Effs my system up, which is probably what happened here also.

---

