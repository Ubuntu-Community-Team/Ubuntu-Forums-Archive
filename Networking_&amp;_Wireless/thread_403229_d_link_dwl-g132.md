---
title: "d link dwl-g132"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by jonny ward9988 on 2007-04-06
hey guys i just installed ubuntu and i love it but i have a small problem.  when i was using windows i used a d link dwl-g132 wireless network adapter and it wokred fine.  but now i have read on the mauel that it wont work on ubuntu so i checked to see if it would work on mac because mac and linux are potentially the same operating system and still found nothing.  i looked around for drivers to fix this problem and havent found anything yet i was wondering if anyone could help me out in giving me some tips or links of sites with a driver that will solve my problem.

thank you

---

### Post by MeneM on 2007-04-06
Hi,

Unfortunatly, your card is not really supported, may I point you to a similar answer I have given to another user just now: [http://ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=403037")

Furthermore, if you search for your card on this page: [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/query_part.php?brandname=D-Link") you will see it is listed as grey. Meaning little to no support.

The card just is not worth the money you paid for I'm afraid.

Setting it up will be tricky now, you will need to go through some hoops to get it to work with things like ndiswrapper. See [this]("http://ubuntuforums.org/showthread.php?t=286530") post.

You will be better off buying a wlan card that is an actual wlan card instead of the software based crap companies sell these days.

---

### Post by jonny ward9988 on 2007-04-06
thank you i appreciate it d link blows and this time im doing it right and running cable from my router directly to my computer for many reasons i would also recomend to anyone out there that is thinking of buying wireless adapters....just buy straight wire it is like 100 times faster and has little to no problems so unless there is no other option dont get a d link!!!!



id also like to thank those people that dedicate there time to help people like me :)

---

### Post by Commensensia on 2007-04-13
Greetings all,

I will state right off the bat that I am by no means a guru and I am pretty close to being a Linux virgin :D.

But I am a bit confused by the statement that the DWL-132 is software based, it is a USB 2.0 format wireless card.
I have never loaded anything but the basic drivers for this card, no special software that I am aware of. And in all honesty it is one of the better pieces I have used, at least in the common joe market of items.

Is there no manner of getting those at Ubuntu to create a working driver for it or it predecessor the DWL-122 also USB based. I have quite a bit invested in the items of my home network, and to be honest since I have became disabled the funds to purchase a new set of home network items is extremely hard to come by, I have actually tried a few Linksys items and quite frankly did not see anything impressive enough to warrant changing over to them.
I also picked up a cheap USB unit being sold under the name of MyEssentials and Ubuntu did not see it either.

I am just not sure that the DWL-132 is software based but I do not have a problem with being wrong either I just would like for someone to point me towards the information that shows it is software based.

Thanks for your time! and any answers you can provide.
Commonsensia :confused:

---

### Post by MeneM on 2007-04-13
Yes, I can certainly understand the question.

You see, the driver in windows does most of the work of encrypting/decrypting, etc of your wireless connection. The hardware merely facilitates what software can't possibly do.

Now if it where a real network card, the hardware would do everything needed to get a wireless connection going, including encrypting/decrypting the packets that flow across the network.

So with software based wireless card, people would mean a card that let's the driver do the lions part of the work needed.

---

