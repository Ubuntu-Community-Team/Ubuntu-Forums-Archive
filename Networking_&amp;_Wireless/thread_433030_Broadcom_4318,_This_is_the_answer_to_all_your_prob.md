---
title: "Broadcom 4318, This is the answer to all your problems!"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by victory2007 on 2007-05-04
Hi all,

I have been struggling with Feisty trying to get my Broadcom BCM4318 card to work.  I found a, and I beleive, The solution to alot of problems.  Go [[COLOR="Blue"]here[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset") and follow the directions step by step and you will get your card working.  Trust me this works.  I have an HP Compaq nx6110 I have tried every trick and posting I can find but this actualy did the trick.  Let me know if it helped you.  Good luck.

---

### Post by stchman on 2007-05-04
> **victory2007 said:**
> Hi all,

I have been struggling with Feisty trying to get my Broadcom BCM4318 card to work.  I found a, and I beleive, The solution to alot of problems.  Go [[COLOR="Blue"]here[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset") and follow the directions step by step and you will get your card working.  Trust me this works.  I have an HP Compaq nx6110 I have tried every trick and posting I can find but this actualy did the trick.  Let me know if it helped you.  Good luck.

That is exactly right.  That is the same procedure I used to get my friends' Broadcom wireless working under Edgy.  Should work under Feisty as well.

---

### Post by H.E. Pennypacker on 2007-05-04
This is not a new method at all.  I believe it has been around for quite a while.  Check out the original thread here:

[http://ubuntuforums.org/showthread.php?t=197102&](http://ubuntuforums.org/showthread.php?t=197102&)

It appears those instructions were put up almost a year ago (June of 2006).  I don't think this method worked for me, though.  I used a similar method, however.

---

### Post by jglen490 on 2007-05-05
That method might work, and probably has for many, but it's not the one that got my 4318-based Buffalo G54 cardbus card to work.

The method that worked on my set up was based on yet another set of instructions found on the Ubuntu Forum.  I used the ndiswrapper and ndiswrapper utils found on my Kubuntu 6.06 install CD.  I also used the Win2K driver set from the Buffalo installation CD.  Then I blacklisted the bcm43xx module that the kernel loads - thus it no longer loads.  Then I followed the standard ndiswrapper setup instructions: ndiswrapper -i <driver file name>, ndiswrapper -m, rebooted, and used kwlan to configure the now lit up Buffalo card for WPA and my wireless router.

Fairly straightforward and relatively "a piece of cake".  Granted this may work for some but not all.  But I have a philosophy about using the tools that already come with the OS whenever possible, avoid compiling unless nothing else works, and apply the simplest solution from the set of possibilities first.

Maybe I was lucky, but then again the results speak for themselves - the darn thing works.

---

