---
title: "Tweaking signal strengh?"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Hadesdarklord on 2008-01-17
Hardware: ACER 7520-5311 laptop with an Atheros AR5007EG wireless card.

Yesterday, an excellent post on this forum allowed me to get my wireless card to work.  Very Good.

My question has to do with signal strength.  Currently, in my office here, I have my laptop, running Ubuntu 7.10, 6 feet from my Linksys wireless router.  It is registering a signal strength of 88%.  (6 feet!)

At home, in my living room, the card will register about 75 - 80% strength (4 out of 5 bars) when running WindowsXP.   Starting up Ubuntu, without moving the machine, I get 44% strength on the same hardware.

This is very curious to me.  I can think of several possible explanations:

1. Mis-reporting signal strength: either Windows is overstating its case, or Ubuntu is understating.

2. Some mysterious hardware issue.

I am just curious if anyone else has noticed this issue, or is it unique to my situation.

Wolf

---

### Post by Scopse on 2008-01-17
I noticed the same thing today while setting up my Netgear DG834G in my kitchen with my main computer set up upstairs. 

I'd get about 38% signal strength in Gutsy and then when I went into Windows I'd get a 'Very Good' connection. After realising I'm not satisfied with 38%, I thought it'd be best to Wire it all up and shed an invisible tear for the £12 I spent on the wireless adaptor.

So really, I haven't helped you at all, just made you aware that your not the only one. Try downloading something in Ubuntu and then switch the Windows and download the same file from the same source and see if you notice any difference in download speed.

---

### Post by Hadesdarklord on 2008-01-18
using my older dell laptop, the ubuntu connection totally overpowers the Windows speed.

However, it is the Atheros Wireless on my new laptop that is giving me issues.

---

### Post by rustybronco on 2008-01-18
> **Hadesdarklord said:**
> 
I am just curious if anyone else has noticed this issue, or is it unique to my situation.
WolfYes,no... but I don't have a clue why, it has been asked before and I haven't found an answer.

---

### Post by terrax on 2008-01-18
Yes and theres is a simple explanation why.

Windows is just adjusting your wireless bandwith, so your signal strengh will go up. My Atheroes have signal strengh 80 % in windows (With 18 mbps bandwith). In ubuntu about 60 % with 54 mbps. Im satisfied with ubuntus way of handling it :-)

By the way. My atheros loos its connection all the time in windows. Got the latest svn snapshot of madwifi, and it just runs great!

---

### Post by Hadesdarklord on 2008-01-19
Thanks Terrax,

I really got the idea that it was the way the information was being reported.

I did several blind tests, with my laptop at various distances from my router.

Even though Ubuntu "reported" a lower signal strength, i could detect no noticable difference in actual throughput.

so, I am satisfied.

Besides, just being able to give my passphrase, instead of typing in my full 26 character wep makes it all worth while.

Wolf

---

